# Project3
Calculator

import tkinter  

root = tkinter.Tk()
root.geometry('400x400')
root.title("calculator")

entry1 = tkinter.Entry(root,width=30)

operators = ['+','-','*','/','=']
entry1.grid(row=0,column=0,columnspan=3)

def update_number(a):

    if a in operators:
        data = entry1.get()[-1]
        if data in operators:
            return 

    entry1.insert(tkinter.END,a)

# label1.pack()

count = 1
for i in range(1,4):
    for j in range(3):
        tkinter.Button(root,text=count,command=lambda a = count: update_number(a)).grid(row=i,column=j)
        count+=1

rows = 1
for i in operators:
    if i =='=':
        continue
    tkinter.Button(root,text=i,command=lambda a = i: update_number(a)).grid(row=rows,column=3)
    rows+=1

def equal_to_operation():
    data = entry1.get()
    new_data = eval(data)
    entry1.delete('0',tkinter.END)
    entry1.insert('0',new_data)
    new_data

for i in [0]:
    tkinter.Button(root,text=i,command=lambda a = i: update_number(a)).grid(row=4,column=1)

equal_to_button = tkinter.Button(root,text="=",command=equal_to_operation)
equal_to_button.grid(row=4,column=2)

def clear_operation():
    data = entry1.get()
    new_data = data[:-1]
    entry1.delete('0',tkinter.END)
    entry1.insert('0',new_data)
    new_data

button_clear = tkinter.Button(root,text="C",command=clear_operation).grid(row=4,column=0)



tkinter.mainloop()
