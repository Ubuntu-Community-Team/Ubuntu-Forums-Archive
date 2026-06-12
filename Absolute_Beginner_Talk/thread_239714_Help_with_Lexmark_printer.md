---
title: "Help with Lexmark printer"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Texan Larry on 2006-08-19
First, let me say, I am sorry I have not found Linux for all this time. Now, the only thing I could not figure out myself was how to get my Lexmark printer to work. I have a z611, I went to Lexmark and downloaded a driver but the system does not recognize it. Any suggestions would be appreciated. 

Linux in Conroe, Texas....:p :D

---

### Post by Big_J on 2006-08-19
You can't download and install windows drivers!

Go to System --> Administration --> Printing
Add a printer, I don't see a z611 but you can try to use one of the other z's and it will very likely work. Test it and if it works make it your default printer.

/Edit
I just saw that they have a driver for linux for the z611, in that case just extract the tar.gz, cd into where the extracted files are and type this into a terminal:
sh z600cups-1.0-1.tar.gz.sh

---

### Post by Texan Larry on 2006-08-19
I tried the one they suggested and it did not work, the download from Lexmark was a Linux download, not a windows. Thanks for the reply.

---

### Post by Big_J on 2006-08-19
You posted while I was editing :)
Did you do it that way, or did you try to double click it or something?

And try the other option I gave you, it will very likely work good

---

### Post by Texan Larry on 2006-08-19
I only tried the one it recommended, I found where they have a very detailed way of doing it, but I am at a total loss on how or where to write the commands it is talking about.  I guess I should use Gnome, but I don't know,

I guess I could always let my Bill Gates and my laptop be my printer, but I would like to have it on the desktop.

---

### Post by Big_J on 2006-08-19
You're not using gnome? What are you using then?
If you aren't sure, then you are probably using gnome, do this:
Applications --> System Tools --> terminal 

If you're using KDE, I'm not sure where you would find it, but it's called konsole

I actually just tried to install it myself, and it wouldn't finish, I'm not sure if it's the problem I've been having these two days which I almost have resolved now, or if it doesn't work on ubuntu... 

Just try to do this for now:
Go to System --> Administration --> Printing
and add a printer

---

### Post by Texan Larry on 2006-08-19
Ahhhhhhhhhh, Ok Big J, I think that is going to help, I will holla later.

Thanks a bunch.

---

### Post by Texan Larry on 2006-08-19
Did not work, I did exactly as you said and it advised Job Stopped,

---

### Post by Big_J on 2006-08-20
oh, that's all I can think of, my printer was on the list so I didn't need to get into it!
Anyone else have any ideas?

---

### Post by gn2 on 2006-08-20
By far the easiest solution is to sell it on eBay and buy one that will work...

---

### Post by indytim on 2006-08-20
Texas Larry,

Let me preface my remarks by stating that I am no expert on the following.  I recommend at a minimum that you consult the WIKI before preceeding.

OK, if you downloaded the deb version of the printer driver from Lexmark, if you right click on the download file, you will see among the options an install option.  Selecting that option should install the driver on your Ubuntu system.  Then, I think it is a matter of adding the printer through the administrative section of your installation.

Note, I have not tried the above.  Hopefully, someone in the know will chime in and either tell me I'm all wet on the advice or make corrections as needed.

At any rate, good luck on your install and report back on the final solution ok?

IndyTim

---

### Post by Texan Larry on 2006-08-20
Indy Tim, thanks, I tried that as well and it did not work, I went as far to try every driver located in add printer, the best I could do is get the paper to feed when I attempted to print a test page, I am at a loss! I tried to follow the instructions located on this site using the Z600 series, and it did not work. I know it is me and a new program, so I press on.  Thank you for the reply.

Texan Larry

---

### Post by givré on 2006-08-20
You should try that :
[http://ubuntuforums.org/showthread.php?t=215657&highlight=lexmark+howto](http://ubuntuforums.org/showthread.php?t=215657&highlight=lexmark+howto)

---

### Post by Texan Larry on 2006-08-20
Do I do that in Root Terminal or any terminal?

---

### Post by givré on 2006-08-20
normal terminal.
If you follow it to the letter, it call sudo when needed.

---

