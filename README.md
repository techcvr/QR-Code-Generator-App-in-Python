# QR-Code-Generator-App-in-Python
How to Make a QR Code Generator App in Python

Hello coders, today i have something interesting python code for you guys, which i found on the internet, i think it is useful for most of the python beginner developers, this is an interesting topic to generate qr code using python .

```python
from tkinter import *
from tkinter import messagebox
import pyqrcode
import os
window = Tk()
window.title("QR Code Generator")

def generate():
    if len(subject.get()) != 0:
        global muQr
        myQr = pyqrcode.create(subject.get())
        qrImage = myQr.xbm(scale=6)
        global photo
        photo = BitmapImage(data=qrImage)
    else:
        messagebox.showinfo("Error!", "Please enter the subject")
    try:
        showCode()
    except:
        pass

def showCode():
    global photo
    notificationLabel.config(image=photo)
    subLabel.config(text="Showing QR Code for: " + subject.get())
def save():
    # folder to save all the codes
    dir = path1 = os.getcwd() + "\\QR Codes"
    # create a folder if not exist
    if not os.path.exist(dir):
        os.makedirs(dir)
    try:
        if len(name.get()) != 0:
            qrImage = myQr.png(os.path.join(dir, name.get() + ".png"), scale=6)
        else:
            messagebox.showinfo("Error!", "File name can not be empty!")
    except:
        messagebox.showinfo("Error!", "Please generate the QR code first")


lab1 = Label(window, text="Enter Subject", font=("Helvetica", 12))
lab1.grid(row=0, column=0, sticky=N + S + E + W)

lab2 = label(window, text="Enter File Name", font=("Helvetica", 12))
lab2.grid(row=1, column=0, sticky=N + S + E + W)

subject = StringVar()
subjectEntry = Entry(window, textvariable=subject, font=("Helvetica", 12))
subjectEntry.grid(row=0, column=1, sticky=N + S + E + W)

name = StringVar()
nameEntry = Entry(window, textvariable=name, font=("Helvetica", 12))
nameEntry.grid(row=1, column=1, sticky=N + S + E + W)

createButton = Button(window, text="Create QR Code", font=("Helvetica", 12), width=15, command=generate)
createButton.grid(row=0, column=3, sticky=N + S + E + W)

notificationLabel = Label(window)
notificationLabel.grid(row=2, column=1, sticky=N + S + E + W)

subLabel = Label(Window, text="")
subLabel.grid(row=3, column=1, sticky=N + S + E + W)

showButton = Button(window, text="Save as PNG", font=("Helvetica", 12), width=15, command=save)
showButton.grid(row=1, column=3, sticky=N + S + E + W)

#Making renponsive layout
totalRows = 3
totalCols = 3
for row in range(totalRows + 1):
    window.grid_rowconfigure(row, weight=1)
for col in range(totalCols + 1):
    window.grid_columnconfigure(col, weight=1)

#looping the GUI
window.mainloop()    
```
 ### Output
 ![image](https://user-images.githubusercontent.com/55651803/114267028-2d4edb00-9a17-11eb-9a21-24d84f8b91e2.png)
