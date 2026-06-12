---
title: "Running programs after install"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by WayOutWest on 2007-05-29
Most programs I have installed like MPlayer and Pidgin have shown up in the start bar, however, programs like kismet and others I can't find or run. any help?

---

### Post by drs305 on 2007-05-29
You may be able to find where the programs are located by typing:
```
whereis yourprogramname
```

Another way to find files on your computer is to run:
```
sudo updatedb
locate yourfilename
```

The first line updates what files are on your computer, the second finds them.

---

### Post by reckless2k2 on 2007-05-29
Kismet and such are usually run in the terminal anyway and you are probably better off running them with sudo permissions.

sudo kismet

---

### Post by WayOutWest on 2007-05-29
right, i found them. i installed them through Adept. but how to I launch/run them? very noobish question i know.

---

### Post by WayOutWest on 2007-05-29
no help? ive found the files and try executing them but nothing happens.

---

### Post by reckless2k2 on 2007-05-29
Open up a terminal window. In your case it sounds like your using Kubuntu so you need to open up a thing that's called Konsole. I believe it's under System or Settings. I'm sorry I can't remember.  I think you can do F2 to bring up the run dialog and type Konsole or Kismet. They are case sensitive so make sure to use lowercase. If you get to the dos like window, type "sudo kismet" without quotes then kismet will begin. From the sound of things, you sound noob to kismet as well which requires that you edit a conf file before you start it anyway. The file must note your wifi card brand in order to work. Get to a terminal window and type lspci and post your output and then i can give you the correct settings in the conf file and or point you to the kismet FAQ that explains what you have to do. You have to jump through a few hoops to get the hacking programs to work.

I can respond more tomorrow as it's my end time soon. ahahaha.

---

