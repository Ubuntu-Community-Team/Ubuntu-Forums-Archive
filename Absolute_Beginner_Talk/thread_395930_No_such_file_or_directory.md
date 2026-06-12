---
title: "No such file or directory"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-03-28
Weird problem. Every time someone suggests to someone in a thread to /etc/hosts or whatever directory they suggest, I do it in terminal and get an error that says NO such file or directory. it's the same error whether I sudo or not, or cd  or just /etc I have tried it WITH a space before the / and without a space. Am I just THAT dense that I'm missing something? I feel like a complete fool when this happens. It's very frustrating as I am trying to do little things that others have had help with, but I am not getting the same results.
It's very frustrating.
Please assist this really stupid NEWBIE!

---

### Post by h0ax on 2007-03-28
I'm not sure I understand your problem fully, but I will give it a go.

if you 
```
 vi /etc/hosts 
```

You get no such file?
The format for moving there in a terminal would be

```
 cd /etc 
```
then ls if you want to list the contents

---

### Post by ComplexNumber on 2007-03-28
as an example, what happens when you type in the following in the terminal:
**cd[COLOR=White]..[/COLOR]/etc**

---

### Post by maccawolf on 2007-03-28
I wish I could figure out what I was doing wrong before, cos now it seems to be working.


don't worry, I'm just a winblows geek who is having a hard time migrating....

Thank you both!:)

---

### Post by h0ax on 2007-03-28
Just make sure you run the command you want followed by the directory/file you want to view/modify.

if you just type /etc/hosts you will get file not found, etc.

Glad to help

---

### Post by maccawolf on 2007-03-28
OK, here's an example. I was trying to get the resources list.
 I put in /etc/apt/resources.list and hit enter, and I get NO SUCH FILE OR DIRECTORY.

---

### Post by h0ax on 2007-03-28
if you want to see what's in your resource list, you need to open it in a text editor
(its sources.list not resources.list)
for example:
```
sudo vi /etc/apt/sources.list
```
if you want to do it in the terminal or
```
sudo gedit /etc/apt/sources.list 
```
if you want to do it in a GUI

---

### Post by ComplexNumber on 2007-03-28
> **maccawolf said:**
> OK, here's an example. I was trying to get the resources list.
 I put in /etc/apt/resources.list and hit enter, and I get NO SUCH FILE OR DIRECTORY.
i receommend that you use nautilus to go to the location (in this case, /etc/apt) and explore the directory before you type anything on the commandline. i do that just to verify that the file is present.



here's a tip: one of the first packages i install after i've just installed a new distro is called the following:
**nautilus-open-terminal**
when this, it means that i can go to a certain location (eg /etc/apt) in nautilus, and if i need to use the commandline in the /etc/apt directory, i just go into the nautilus menu and select 'open terminal. a screenshot will show you what i mean. your terminal then appears in that directory exactly if you'd put cd /etc/apt in there instead.

---

### Post by maccawolf on 2007-03-28
OK, REALLY stupid question. WHat do you mena by doing it in a GUI. I know what GUI is for winblows, and I imagine it;s the same in linux, but HUH??????


I thought Nautilus was another browser like FF or Opera or somthing

---

### Post by h0ax on 2007-03-28
Nice solution ComplexNumber

That is very helpful for people who aren't familiar with the command line interface.

I wrote it down for future helping of new users.

---

### Post by h0ax on 2007-03-28
Nautilus is your File Explorer - it's like My Computer -> C: -> Program Files, etc. in Windows.

GUI is Graphical User Interface (It's something you can move around, like Notepad) whereas when you do something in the terminal (command line) you're working on the file in the same place you're doing commands (like DOS)

Hope this helps

---

### Post by maccawolf on 2007-03-28
Just as a point of information, I got NOTHING with sudo gedit /etc/apt/sources.list

It DID ask for my password, but then it just hung there and eventually gave me the lobo@lobo:~$ prompt again.

---

### Post by maccawolf on 2007-03-28
so then what's the difference between NAutilus and PLACES on the toolbar?

And Where IS Nautilus?

---

### Post by h0ax on 2007-03-28
Gedit is a text editor generally included in base install of ubuntu with the GNOME package.
Nautilus is File Explorer - PLACES on toolbar takes you to your home folder (like My Documents in Windows)

If you don't have gedit or something is wrong with it it won't open the file properly.

Places -> Computer will show you like My Computer

Places on the toolbar will open Nautilus at that designated location.

---

### Post by maccawolf on 2007-03-28
OK, so we can maye ASSUME that there is a problem with gedit, How do I find it and determine if it's ()*)_&+* AND fix it if it;s a problem?

---

### Post by h0ax on 2007-03-28
Sorry, I was away.

Have you tried Applications -> Accessories -> Text Editor

does anything happen?

---

### Post by NicoleM on 2007-03-28
removed

(realized my post wasn't relevant...couldn't make out how to delete it.  ignore this please)

---

### Post by maccawolf on 2007-03-29
Hoax (you may have been away, but I started falling asleep, so I shut down...)

When I open text edit, it acts just like Notepad in Winblows. Nothing HAPPENS.......
Is there something special I'm supposed to do?

---

### Post by Outrunner on 2007-03-29
After you type

```
gksudo gedit /etc/apt/sources.list
```

It will ask you for your password. Type it and press enter. Yes you can't see what you type. It's a security method.

---

### Post by STREETURCHINE on 2007-03-29
not to confuse you but it should be.

       ```
gksudo gedit /etc/apt/sources.list
```

you should use gksudo for all graphical applications

---

### Post by Outrunner on 2007-03-29
> **STREETURCHINE said:**
> not to confuse you but it should be.

       ```
gksudo gedit /etc/apt/sources.list
```

you should use gksudo for all graphical applications

Yes, you're right of course. I always forget to do gksudo instead of just sudo. Edited my post, thanks.

---

### Post by h0ax on 2007-03-30
Hey there macca,

Sorry it's been a minute since I was on, when you try their
>  gksudo gedit /etc/apt/sources.list

Does anything happen?

( I have to go to class, but I will check later ) Let's fix it.

---

### Post by maccawolf on 2007-03-30
thanks all, will try this when I get home.

---

### Post by h0ax on 2007-04-01
Any luck?

---

### Post by maccawolf on 2007-04-01
H0ax,

 I had luck for two days.
I spent all day yesterday reading different things to try to correct a couple of different problems. (Hal error is back that I thought was fixed a few days ago). Now when I do the rc.d update thingy it doesn't change the error (it worked several days ago. Also tried replacing my sources list with the one from the Wiki, and that didn't work either. I am VERY close to reinstalling Ubuntu and stating from scratch, but I'm gonna go do my laundry first and do some more reading from my Ubuntu unleashed book first.....


PS. Very frustrated camper here,.........

---

