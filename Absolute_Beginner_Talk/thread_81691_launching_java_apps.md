---
title: "launching java apps"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by RevNomad on 2005-10-25
How do I do this.  Preferably from an icon.  

Thanks in advance
Norman

ps
Yes, Java is installed.

---

### Post by Beggar on 2005-10-25
java apps, are you referring to jar files, class files, jnlp's, can you be a little more specific?

---

### Post by RevNomad on 2005-10-25
See?  That's just the point I didn't know I needed to be more  specific.:confused: 

Jar files.  (They're the only ones I even begin to know how to use.  In Windows I create a batch file, then link the batch file to a short cut.  On linux what do I do?

NTP

---

### Post by KLineD on 2005-10-25
The same. make a text file with gedit and type:
```

java -jar nameofjar.jar

```

Now save the file and set the executable flag. To do this you can right click the file, properties, permissions. There check the box that says Execute, OR you can do it in the console just type chmod +x nameoftextfile

Now your text file is the 'batch' to execute the jar. You can make a shortcut to the text file in your desktop or whatever.

Hope this helps.

---

### Post by RevNomad on 2005-10-25
Thanks, the first straight answer I've gotten or found on that.  This seems one of those items "Everyone knows."  NTP

---

### Post by Sladi on 2007-05-06
Hi! 

I tried create a launcher but this doesn't work. When I double cklick on the file in Nautilus the program starts but whenI make a launcher wich points to the file, nothing happens. 
How can I make it work? The program is Semicuro. 


Regards, 
Sladi

---

