---
title: "Command line"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-11
Is the command line and the Terminal the same thing?

I tried to install the ndiswrapper, but I can't manage to...
In the wiki it tells me to "download it and extract it with: 
"tar zxvf ndiswrapper-version.tar.gz"".

Where do I save the gz file in order for the command to work? and where do I write the command? is it indeed the terminal? if it's the terminal what does it mean to go to the directory where it's saved and then write it?

thanks,:) 
Joshua

---

### Post by NeghVar on 2006-04-11
Download the file, lets use your Deskotp for reference.

You can do it without the command line by just going to your desktop, create a folder, move the tar to that folder, then right click then extract here.

For CLI go Applications>Accesories>Terminal.

To get to the Desktop type:

cd ~/Desktop
hit enter
tar zxvf ndiswrapper-version.tar.gz
hit enter again

---

### Post by taurus on 2006-04-11
When you download something to your computer using firefox, you have to tell firefox where to save it to.  If you use the default, then it will be saved to ~/Desktop.  By the way, ~ means your home directory.  In other words, if your login name is Caligula, then ~ is the same as /home/Caligula.  You can open a terminal by clicking on Applications -> Accessories -> Terminal and at the prompt, type
```

cd ~/Desktop

```
Now, you need to unpack it as
```

tar zxvf ndiswrapper-version.tar.gz

```
Now, just follow the instructions on wherever you download it to install ndiswrapper for your wireless card.  By the way, terminal is where you type the command so to be able to type something, you need to open a terminal first so you can say that they are the same.

---

### Post by Caligula on 2006-04-11
[QUOTE=taurus]When you download something to your computer using firefox, you have to tell firefox where to save it to.  If you use the default, then it will be saved to ~/Desktop.  By the way, ~ means your home directory.  In other words, if your login name is Caligula, then ~ is the same as /home/Caligula.  You can open a terminal by clicking on Applications -> Accessories -> Terminal and at the prompt, type
```

cd ~/Desktop

```
Now, you need to unpack it as
```

tar zxvf ndiswrapper-version.tar.gz

```
Now, just follow the instructions on wherever you download it to install ndiswrapper for your wireless card.  By the way, terminal is where you type the command so to be able to type something, you need to open a terminal first so you can say that they are the same.[/QUOTE]

Thanks, it worked, or, I managed the first command...
after that I'm supposed to go to the source directory, is it where the ndiswrapper is extracted to?
That's where I went, and put "make distclean" in the terminal, it said the command is not found... screenshot attached

Any ideas?

---

### Post by taurus on 2006-04-11
You need to install build-essential first before you can build anything on your system.  Type this from a prompt,
```

sudo apt-get install build-essential

```
Then, run your commands again...

---

