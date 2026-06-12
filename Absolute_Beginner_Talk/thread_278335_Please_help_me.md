---
title: "Please help me"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by vladimir007 on 2006-10-16
Hello,

	How can i save the file "wvdial.conf" located at /etc/ ?

	Whenever i try to save it using "ctrl+s", it says 
	"permission denied"

	Which commands are used to dial the modem through terminal?
	( gnome ppp)

	Can anybody help me?

---

### Post by wieman01 on 2006-10-16
> sudo gedit /etc/wvdial.conf
Type in your user password when prompted. Run this command from command line (terminal). The prefix "sudo" lets you perform administrative tasks as if you were "root".

---

### Post by ojasvi rajpal on 2006-10-16
In case of any such problems use the command prompt and prefix any command u wanna run by " sudo ". like $ sudo vi file_name

---

