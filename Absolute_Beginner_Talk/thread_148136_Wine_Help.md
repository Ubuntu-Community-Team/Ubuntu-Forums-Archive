---
title: "Wine Help"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Crud on 2006-03-21
I am running Ubuntu and have installed wine.  I would like to try to run a windows application but can't seem to tell it how to get to the file.  Windows is mounted and is on /dev/hda1. I can click on the windows icon and see all of the contents of the file system (windows).  But, for example, when I try to specify where the file is located which is (I think) 
"c://Program Files/e-Sword/e-sword.exe" the bash shell gets to the blank in Program files and sees that as the delimiter and stops parsing.  It has been a while since I have used Unix or lynix to any extent and I'm rusty.  Can anyone please help me get going thru this snag? Thanks,

---

### Post by bergersau on 2006-03-22
In general (And I'm no expert)

After installing wine.
Run the following.

winecfg    -  to setup the wine environment.
wine ./application_installer  (Assuming the windows application installer is in the current directory.)

to run the app you'll need to run somthing like.

wine '/home/username/.wine/c_drive/program files/.../application.exe'  

(This will need to be the exact path wine has installed the app to.  Please note that .wine is a hidden directory.)

Hope this helps.

Dan

I'm going from memory here so don't just cut and paste these commands - they are probably incorrect in minor ways and you'll need to put in your own filenames etc.  They should point you in the right direction though.

I think you've been trying to run an app installed on a REAL windows partition as opposed to the virtual windows drive that wine creates in your linux home directory.

---

### Post by KansasJoe on 2006-03-22
I couldn't get esword to run on mine so you may want to try bibletime (kde) or gnomesword....bibletime is very nice and you can select which bibles and commentaries you want....works identical to esword and runs natively on linux....still no NIV though because they won't just give it away

---

### Post by Marshall2day on 2006-03-22
[QUOTE=Crud]the bash shell gets to the blank in Program files and sees that as the delimiter and stops parsing.,[/QUOTE]

Put a backslash in front of the space to escape it.

---

### Post by trorion on 2006-03-22
[QUOTE=Crud]I am running Ubuntu and have installed wine.  I would like to try to run a windows application but can't seem to tell it how to get to the file.  Windows is mounted and is on /dev/hda1. I can click on the windows icon and see all of the contents of the file system (windows).  But, for example, when I try to specify where the file is located which is (I think) 
"c://Program Files/e-Sword/e-sword.exe" the bash shell gets to the blank in Program files and sees that as the delimiter and stops parsing.  It has been a while since I have used Unix or lynix to any extent and I'm rusty.  Can anyone please help me get going thru this snag? Thanks,[/QUOTE]

```
$ wine /dev/hda1/Program\ Files/e-Sword/e-sword.exe
```
OR
```
$ wine /dev/hda1/"Program Files"/e-Sword/e-sword.exe
```

Your choice.

---

