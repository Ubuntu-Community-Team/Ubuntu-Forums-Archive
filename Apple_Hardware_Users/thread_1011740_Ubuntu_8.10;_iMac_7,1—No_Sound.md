---
title: "Ubuntu 8.10; iMac 7,1—No Sound"
date: 2008-12-15
forum: Apple Hardware Users
---

### Post by Stasven on 2008-12-15
I've read all of the F.A.Q.s and have searched Google near and far but have yet to find a solution to my problem. I've installed Ubuntu 8.10 onto my iMac 7,1 and I am receiving no sound. 

Can anyone please help me without just referring me to an F.A.Q.?

---

### Post by bryonak on 2008-12-15
What does lspci give you?

It would be helpful if you mentioned which FAQs and commands you tried, because it's quite hard to diagnose a problem from your first posting. Not all Apple users here are familiar with iMacs (at least I'm not), so they don't know what hardware it uses.
Also mention whether you feel uncomfortable with the terminal so that we should give you the the exact commands instead of writing them in prose (like my question above).

---

### Post by cyberdork33 on 2008-12-15
Run "alsamixer" in a terminal and make sure that your channels are unmuted and turned up.

You might also need to do this:
[https://help.ubuntu.com/community/Intel_iMac#Sound](https://help.ubuntu.com/community/Intel_iMac#Sound)

---

### Post by Stasven on 2008-12-15
I'm not very confident with Terminal actually. I don't understand that last walk-through you linked, cyberdork33. It's all just really annoying now...

---

### Post by cyberdork33 on 2008-12-15
> **Stasven said:**
> I'm not very confident with Terminal actually.and you won't be unless you use it. alsamixer is a console program, but it has a graphical interface... just run the command and you will see what I mean.

> **Stasven said:**
> I don't understand that last walk-through you linked,cyberdork33. It's all just really annoying now...

It means to open the file located at /etc/modprobe.d/options with a text editor. The command shown will do that for you:
```
sudo nano /etc/modprobe.d/options
```

then add the text "options snd-hda-intel model=imac24" to the file and save it and reboot.

---

### Post by Stasven on 2008-12-16
> **cyberdork33 said:**
> and you won't be unless you use it. alsamixer is a console program, but it has a graphical interface... just run the command and you will see what I mean.



It means to open the file located at /etc/modprobe.d/options with a text editor. The command shown will do that for you:
```
sudo nano /etc/modprobe.d/options
```

then add the text "options snd-hda-intel model=imac24" to the file and save it and reboot.

I used alsamixer and the volume was at 98%. Also, I opened that "/etc/modprobe.d/options" in Terminal but I didn't understand the programme that it opened. I read that I'm supposed to add the text to it, but where in the file?

---

### Post by bryonak on 2008-12-16
If you have problems understanding what *any* thing means, just ask. It will be answered politely, instead of frustrating everyone when someone asking for help does so by "Something doesn't work, help me!" (just speaking generally now).

It makes it easier for those who help to know if the user knows what prepending "sudo" to a command does... but enough of that, let's give some help.


You can open any program in the terminal just by typing it's name (for example firefox). nano is Ubuntu's standard command line text editor, gedit is the standard graphical text editor. If you like gedit more, you can either open it by clicking on Applications -> Accessoires -> Text editor  or by just typing **gedit** into a terminal.
This way, you can open the modules file by ```
gksudo gedit /etc/modprobe.d/options
```
According to the HowTo cyberdork linked to, you should now just make a new line (for example at the bottom) and add this to it:
```
options snd-hda-intel model=imac24
```



If you prefer a simple alsamixer GUI, just type this into a terminal (and ask if you don't understand what the command means **)
```
sudo aptitude install alsamixergui
```
The same can be accomplished by clicking on System -> Administration -> Synaptic Package Manager  and there Search -> "alsamixergui" -> right click -> Mark for installation -> Apply
It's just that in this case, doing it with the terminal is much, much faster.
You can then open the program either in Applications -> Sound&Video -> alsamixergui ... or just type the name into a terminal ;)


The command **lspci** will list the devices connected to the PCI interfaces of your mainboard, which I asked you to issue in order to see what audio hardware you have.



** We had cases here where people disguised commands to delete all the users files as "help", if executed blindly without understanding. You should at least have some basic idea what a command you found on the internet does.

---

### Post by cyberdork33 on 2008-12-16
> **bryonak said:**
> ```
sudo gedit /etc/modprobe.d/options
```

Just a note, if you open a gnome application, you should use gksudo in place of sudo. This will keep config files from becoming modified with root permissions (and later having issues when trying to use the app as a normal user).

---

