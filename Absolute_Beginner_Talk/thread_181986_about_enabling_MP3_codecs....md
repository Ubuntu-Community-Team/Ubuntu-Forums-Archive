---
title: "about enabling MP3 codecs..."
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Solidad on 2006-05-25
i read the restricted format, section and still i can't figure out how to install it.

i dont see the packages listed in the guide. 

so i need to have a internet connection to enable these software is there a more layman way of saying how to do this?

---

### Post by nalmeth on 2006-05-25
You likely haven't enabled the required repositories.

Hit ALT-F2

type:
gksudo gedit /etc/apt/sources.list

remove the ## from the front of the repositories you need

You may prefer to use automatix, many do. See the link in my signature.

---

### Post by Sef on 2006-05-25
Do you or do you not have an internet connection?

---

### Post by Solidad on 2006-05-25
i dont have a internet connection on ubuntu but i have on windows (Dial-up)

the automatix link is broken.

---

### Post by nalmeth on 2006-05-25
OK, it wasn't clear that you didn't have Ubuntu internet.
Sorry about my sig link, and thanks for pointing it out, it's corrected now.
What you might want instead is the [automatix CD]("http://www.ubuntuforums.org/showthread.php?t=145889")

---

### Post by Solidad on 2006-05-25
its a iso image. i am using a dial up and. i dont have a burner yet. what are the other options?

---

### Post by Koech on 2006-05-25
Is ther no way you can connect the Ubuntu box to dialup too? If possible you can do this much easily I suppose.

---

### Post by Solidad on 2006-05-25
i have a winmodem so i am trying to do my best in enabling this option.

---

### Post by Sef on 2006-05-25
Check out [linmodems.org/]("http://linmodems.org/")  

They have a lot of info on getting to run winmodems on Linux.

---

