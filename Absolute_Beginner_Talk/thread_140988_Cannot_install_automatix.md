---
title: "Cannot install automatix"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by stravinsky on 2006-03-07
Hello everyone!

I'm completely new to Ubuntu and have recently discovered that Automatix is a very good program. I have manage to download it through the terminal, but when I follow the instructions (dpkg -i automatix[version].deb) in order to install it, it stops and says that it is not a supported debian package. I have tried with several versions already.

My Ubuntu version (Breezy) has never been updated through the internet, in case this might give an explanation to my problem.

Thank you for your help.

---

### Post by LordBug on 2006-03-07
Did you try running it with sudo?  Dpkg requires root level access in order to function properly.  Try "sudo dpkg -i automatix[version].deb"

---

### Post by stravinsky on 2006-03-07
Yes, I've forgotten to mention that I was using "sudo dpkg etc."
Thanks.

---

### Post by LordBug on 2006-03-07
I'd suggest attempting to re-download then.  You might have a bad copy.

If it still errors, please post the entire message you get (copy and paste, preferably).

---

### Post by stravinsky on 2006-03-08
I'm surprised no one has got the same problem...
I have tried to download it again from Windows, but it won't work using this url: [http://www.beerorkid.com/automatix/automatix_5.5-5_i386.deb](http://www.beerorkid.com/automatix/automatix_5.5-5_i386.deb)
Can someone send it to me?

When I have previously downloaded automatix, it would appear as html type when exploring the file with "sudo nautilus".

I cannot unfortunately give you the full text of the error, as I do not have my computer (that has Ubuntu) with me right now. But it just says something like "cannot install because not a debian package".

Apart from this, when I will finally manage to install automatix, will I need to be connected to the internet to use it?

Thanks.

---

### Post by Mustard on 2006-03-08
[QUOTE=stravinsky]I'm surprised no one has got the same problem...
I have tried to download it again from Windows, but it won't work using this url: [http://www.beerorkid.com/automatix/automatix_5.5-5_i386.deb](http://www.beerorkid.com/automatix/automatix_5.5-5_i386.deb)
Can someone send it to me?

When I have previously downloaded automatix, it would appear as html type when exploring the file with "sudo nautilus".

I cannot unfortunately give you the full text of the error, as I do not have my computer (that has Ubuntu) with me right now. But it just says something like "cannot install because not a debian package".

Apart from this, when I will finally manage to install automatix, will I need to be connected to the internet to use it?

Thanks.[/QUOTE]


You will need to be connected to the internet, yes.

Questions about automatix might be better directed to the Automatix section of the forum, under Third Party Projects.

---

### Post by stravinsky on 2006-03-08
Do you mean that it is not installable without being connected on the internet?

I've now asked my question under the following post: [http://ubuntuforums.org/showthread.php?t=135066](http://ubuntuforums.org/showthread.php?t=135066)

Thanks.

---

### Post by Papa-san on 2006-03-08
How do you download something through a terminal? I hate to jump in to the middle of your thread, but I read something about this 'automatix' thing, but that's as far as it got... Following the instructions got me nowhere...

---

### Post by Mustard on 2006-03-08
[QUOTE=Papa-san]How do you download something through a terminal? I hate to jump in to the middle of your thread, but I read something about this 'automatix' thing, but that's as far as it got... Following the instructions got me nowhere...[/QUOTE]

I'm not exactly sure if this is what you are asking, but you use the **wget** command to download things in terminal.

This command will bring up the wget manual in the terminal..

```
man wget
```

Press the 'q' key to exit the manual.

An example of a wget command would be..

```
wget http://www.somewebsite.com/downloads/filename
```

---

### Post by Mustard on 2006-03-08
[QUOTE=stravinsky]Do you mean that it is not installable without being connected on the internet?

I've now asked my question under the following post: [http://ubuntuforums.org/showthread.php?t=135066](http://ubuntuforums.org/showthread.php?t=135066)

Thanks.[/QUOTE]

I don't use automatix myself, so I don't know all the details about installation (hence my recommendation to go to the forum that covers this project).  When it is installed however, it will need to access online repositories to install the packages, so a working internet connection is pretty fundamental to using it with any great success.

---

