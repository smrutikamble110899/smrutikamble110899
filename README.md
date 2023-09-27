from tkinter import *
import tkinter.messagebox as msg


class Multiple():
     def __init__(self,root):
         self.root=root
         self.root.title("library management system")
         self.root.config(bg="powderblue")
         title = Label(self.root,text="home page",bg="powderblue",font=('bold','25'))
         title.pack()

         admin_button=Button(self.root,text="admin",font=('bold','18'), command=self.admin_page)
         admin_button.place(x=500,y=150)

         user_button=Button(self.root,text="user",font=('bold','18'))
         user_button.place(x=500,y=220)

     def  admin_page(self):
         window = Tk()
         window.title("Admin page")
         window.geometry("300*300")
         window.config(bg="powderblue")

         book_name_Label = Label(window, text="book_id", bg="powderblue", font=('bold', '50'))
         book_name_label.place(x=20, y=40)

         author_label = Label(window, text="author name", bg="powderblue", font=('bold', '15'))
         author_label.place(x=20, y=100)

         qty_label = Label(window, text="quantity", bg="powderblue", font=('bold', '15'))
         qty_label.place(x=20, y=160)

         self.book_entry = Entry(window)
         self.book_entry.place(x=180, y=40)

         self.author_entry = (window)
         self.author_entry.place(x=150, y=100)

         self.qty_label = Entry(window)
         self.qty_entry.place(x=150, y=160)

         label= Button(window, text="submit",command=self.admin_data)
         label.place(x=120, y=200)

     def admin_data(self):
         import mysql.connector

         mydb = mysql.connector.connect(host='localhost',port=3306,user='root',password='Smruti@11',databases='library_management')
         mycursor = mydb.cursor()

        bookname=self.bookname_entry.get()
        author=self.author_entry.get()
        qty=self.quantity_entry.get()

        mycursor.execute("insert into admin value(%s,%s,%s)",(bookname,author,qty))
        mydb.commit()
        msg.showinfo("admin books","book added to stock")
root = Tk()
object = Multiple(root)
root.mainloop()

