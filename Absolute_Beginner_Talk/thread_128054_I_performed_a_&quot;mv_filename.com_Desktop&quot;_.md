---
title: "I performed a &quot;mv filename.com /Desktop&quot; &amp; lost it!!!"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-10
Hello everybody.

I am new to Linux & trying to learn it, but it is hard to do so.
However I am still trying my best.

Now, my problem is this:

I opened a Windows formatted floppy disk in Linux.

I saw the contents & at some point wanted to MOVE a file from the Floppy to my Desktop.

I performed the command:

                                                    "mv filename.com /Desktop".

With the above command, I lost the file from the Floppy (good part), but I can not seem to find the file in the Desktop (bad part)...

I also checked "Home" & "File System" folders, and it is not there either.

Can anybody tell me, where might the file be?

Thanks in advance,

Dimitris.

---

### Post by Pragmatist on 2006-02-10
Are you sure the file isn't still on the floppy??  Have you checked it again in Windows?

---

### Post by Lord Illidan on 2006-02-10
I am guessing that in your harddrive, there is now a file called /Desktop in the root folder, i.e. "/"

Check it.

To move a file to the desktop from the terminal, either use a GUI, ie Gnome or KDE..
or else, do this : ```
cp *name of filename* /home/*your name*/Desktop/
```

Note, cp will copy, mv will move or rename..



To help, while entering the command, pressing TAB will autofill.

---

### Post by Pragmatist on 2006-02-10
Forgot to ask.  Are you looking for the file on your desktop?  Because your user desktop is located in /home/username/Desktop  So if your regular username is reguser  it would be at /home/reguser/Desktop  or if you are root you'd put it at /root/Desktop

But, you put it at: /Desktop  There is no such directory, so try:
```
cd /
```
```
ls -l Desktop
```

---

### Post by dvarsam on 2006-02-10
Feedback from Author:

Yes, a folder named "Desktop" is now in the root folder.

However, when I type "cd Desktop", it says "Desktop: Not a directory".
So, basically I can not access the root Desktop.

So, how do I move a file from a Windows floppy to the Linux Desktop?

There is no MOVE command?

You are suggesting to COPY it & then Delete the File from the Floppy?

And, now can I remove the Desktop from the root?

---

### Post by nrwilk on 2006-02-10
The command you issued would put the file into the root (/) directory with a name of "Desktop".  Except to do this, you would have had to have root privledges.  So, I don't know how you did it, unless you had a "sudo" in front of the command which you executed.

the command you should have issued was:
```
mv <filename> /home/<username>/Desktop/
```

Also, one of the first things you learn in a unix class, for this exact reason, is to NEVER use the mv command, except to rename things.  Instead, it's much safer to use "cp" and then "rm" the original once you've verified that the copy safely arrived in the desired location.

Check and see if you have a new file located at / that's called "Desktop."  There's your file.

---

### Post by Pragmatist on 2006-02-10
You can name a file virtually anything.  So you named your file Desktop.  So /Desktop is the location of your file (the one you moved from your floppy).  If you want to put that file on the desktop open a terminal and type:
```
cp /Desktop /home/your_name/Desktop
```
Then since you are still logged in as root, logout and login as a regular user and you'll see the file on your real Desktop.

---

### Post by nrwilk on 2006-02-10
[QUOTE=dvarsam]Feedback from Author:
However, when I type "cd Desktop", it says "Desktop: Not a directory".
So, basically I can not access the root Desktop.
[/QUOTE]
This is because you created a file called Desktop, it isn't a directory.

---

### Post by dvarsam on 2006-02-10
Thank you guys, you were all correct!!!

I gave the file it's original name & moved it back to the Floppy.


I hope Windows will be able to recognise the file.

Thanks again.

---

### Post by nrwilk on 2006-02-10
Sure thing!  I like it when I find a thread I can help out on (this is rare).

Also, Windows should be able to read the file.  *nix systems are really good at preserving bits in stored data.

---

