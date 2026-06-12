---
title: "Gnome Gui File Permisions"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by mtbiker on 2006-01-05
Hello,
  How do I add files or folders to a directory other than my home directory (/var/www/) for example.  I just want to create a simple test html and php file but when I right click in the folder /var/www/apache2 Create folder and create file is greyed out?  I'm guessing this is a permissions issue, I just don't know how to get around it with out using vi thru the terminal as root.

Thanks
Mark

---

### Post by super on 2006-01-05
you can run nautilus as root by typing [FONT="Courier New"]gksudo nautilus --no-desktop --browser[/FONT] in a terminal window.

be very careful tho!

---

### Post by mcmillan on 2006-01-05
You mention not using vim, would it make sense to use gedit. You can use ```
sudo gedit [name of new file]
``` to create and edit a file. Also if you already have a file you want to move you can do it with ```
sudo mv [location of source] [new location]. 
```

---

### Post by mtbiker on 2006-01-06
That works.  Thanks for your help.

---

