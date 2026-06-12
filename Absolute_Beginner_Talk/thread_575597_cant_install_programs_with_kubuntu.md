---
title: "cant install programs with kubuntu"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by stvdel on 2007-10-14
Hello, I installed Kubuntu 7.04 with Wubi and everything has worked fine I downloaded firefox and went to the terminal to install and entered the command and then it asked me for my password but it would not let me type anything it just froze. Does anyone know why this is happening or how to run a command without it asking for a password. Thanks

---

### Post by bubbalouie on 2007-10-14
It doesn't display anything, type, press enter, and it should work (unless you miss type the password)

---

### Post by RudolfMDLT on 2007-10-14
What command did you type in? an yeah - for security reasons and to confuse people new to Linux the "password:" line doesn't show anything! :) If you ever get stuck, press CTRL+C and the program in the terminal will stop.

Cheers,

Rudolf

---

### Post by stvdel on 2007-10-16
Yes you are right it doesnt display the password, I thought something was not working I am new to this. Although I wonder now, I am trying to install firefox and I am trying to add some code to the firefox file using kate but now it will not let me save or overwrite the file it says I cant write to the disk, like I have said before I am using kubuntu through wubi. Any suggestions.

---

### Post by Incense on 2007-10-16
I would just grab firefox from the repos

```
sudo apt-get install firefox
```

---

### Post by gossrock on 2007-10-16
"sudo apt-get install firefox"  will install firefox from the repositories you will not need to download anything from the firefox website.  But it should be installed by default so there should be no need to do it at all.  

If it is not installed for some strange reason then you can do the same thing as "sudo apt-get install firefox" in a graphical way by going to the Aplications window and choosing "Add/Remove..." and then search for Firefox.  

A third way to do it is that you can go the System menu and go to the Administion sub menu and pick "Synaptic Package manager" and then again search for firefox and check the box next to the firefox package and the click the "apply" button.

But again, really you should not have to install firefox.  Just click the firefox logo on the top of you screan and serf away, if for some reason you accidentally delleted the launcher from the top pannel then you can go to the Aplication menu and then to the internet submenu and then you should see the firefox logo/launcher from there.

---

### Post by gossrock on 2007-10-16
oops, just realized you were talking Kubuntu, sorry my response related to were things were was all Ubuntu related and It's been along time since I've used Kubuntu so I don't know were things are...  I also am not sure if it is even enstalled on Kubuntu by default.  ... 

but regardless "sudo apt-get install firefox" should work regadless of the Ubuntu derivative.

---

### Post by stvdel on 2007-10-17
yes, it is not installed by default in kubuntu. thanks for the help with this although i found all i
have to do is run the sudo kate so it gives me the proper access to edit the file. thanks again.

---

