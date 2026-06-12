---
title: "Quake Wars Demo Install Problem"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Dapilot1 on 2007-11-01
So I downloaded the file and the md5 matches, but after running this code.
```
 sudo sh '/home/lewis/Downloads/Torrents/ETQW-demo-client-1.1-full.r5.x86.run' 
```
I get this response.
```
 /home/lewis/Downloads/Torrents/ETQW-demo-client-1.1-full.r5.x86.run: 1: Syntax error: "(" unexpected 
```
Am I doing something wrong? How do I install this demo?

---

### Post by Crafty Kisses on 2007-11-01
> **Dapilot1 said:**
> So I downloaded the file and the md5 matches, but after running this code.
```
 sudo sh '/home/lewis/Downloads/Torrents/ETQW-demo-client-1.1-full.r5.x86.run' 
```
I get this response.
```
 /home/lewis/Downloads/Torrents/ETQW-demo-client-1.1-full.r5.x86.run: 1: Syntax error: "(" unexpected 
```
Am I doing something wrong? How do I install this demo?

Make sure it's in the right directory, and the directories are case sensitive. :)

---

### Post by Dapilot1 on 2007-11-01
It it definitely the right directory because I drag and dropped it in to the terminal. That is why there are '' around it. I tried opening it up in gedit to see if there was a ( floating around somewhere, but it is too big for me to wait while it opens.

---

### Post by Maestro23 on 2007-11-01
> **Dapilot1 said:**
> It it definitely the right directory because I drag and dropped it in to the terminal. That is why there are '' around it. I tried opening it up in gedit to see if there was a ( floating around somewhere, but it is too big for me to wait while it opens.

Just navigate to the directory itself and then run the script.

---

### Post by Dapilot1 on 2007-11-01
I tried that and got the same error.

---

### Post by Maestro23 on 2007-11-01
> **Dapilot1 said:**
> I tried that and got the same error.

Did you make it executable first?

> sudo chmod a+x ETQW-demo-client-1.1-full.r5.x86.run

Can also do it in Nautilus.  Right-click on the file, goto Properites, Permissions (Make Executable).

Forgot the sudo, as 2point0 pointed out.

---

### Post by The Tronyx on 2007-11-01
First:
> 
sudo chmod +x ETQW-demo-client-1.1-full.r5.x86.run


Then
> 
./ETQW-demo-client-1.1-full.r5.x86.run 


Let me know if that helps.

---

### Post by Dapilot1 on 2007-11-01
No, but I did now and I'm still getting the same error.

---

### Post by Dapilot1 on 2007-11-01
When I right click and go to properties, it says next to type that it is an executable.

---

### Post by The Tronyx on 2007-11-01
> **Dapilot1 said:**
> When I right click and go to properties, it says next to type that it is an executable.

And what are the file's permissions set to when you right click on it and look at the properties?

---

### Post by Dapilot1 on 2007-11-01
Owner: lewis - (My full name)
Access: Read and write

Group: lewis
Access: Read-only

Others
Access: Read-only

Execute: [checked] Allow executing file as program

SELinux Context: unknown
Last changed: Thu 01 Nov 2007 09:27:15 PM CDT

I don't know if this makes a difference, but the icon for this file is different than the icon on the old school ET. It shows a file with 1 and 0's instead of the terminal icon.

---

### Post by The Tronyx on 2007-11-01
Can all users groups and others execute the program?

If you type:

ls -l ETQW-demo-client-1.1-full.r5.x86.run

What do you see?

---

### Post by oldos2er on 2007-11-01
From within Nautilus, right-click on the file, choose Permissions, and make sure it's set to Read and Write under Owner and Group.

---

### Post by Dapilot1 on 2007-11-01
Before oldos2er's advice:
-rwxr-xr-x 1 lewis lewis 674511145 2007-11-01 19:21 ETQW-demo-client-1.1-full.r5.x86.run

After:
-rwxrwxrwx 1 lewis lewis 674511145 2007-11-01 19:21 ETQW-demo-client-1.1-full.r5.x86.run

Still does not work.

---

### Post by The Tronyx on 2007-11-01
> **Dapilot1 said:**
> Before oldos2er's advice:
-rwxr-xr-x 1 lewis lewis 674511145 2007-11-01 19:21 ETQW-demo-client-1.1-full.r5.x86.run

After:
-rwxrwxrwx 1 lewis lewis 674511145 2007-11-01 19:21 ETQW-demo-client-1.1-full.r5.x86.run

Still does not work.

What command are you trying to run it with?

---

### Post by Dapilot1 on 2007-11-03
Right after downloading I put this in and nothing else.
```
 sudo sh ETQW-demo-client-1.1-full.r5.x86.run 
```

Or if you were talking about how to change the permissions, all I did was right click and change the settings.

---

### Post by Maestro23 on 2007-11-03
> **Dapilot1 said:**
> Right after downloading I put this in and nothing else.
```
 sudo sh ETQW-demo-client-1.1-full.r5.x86.run 
```

Or if you were talking about how to change the permissions, all I did was right click and change the settings.

Just download this earlier today.  Changed the file permission and then:

> ./ETQW-demo-client-1.1-full.r5.x86.run 

Took me into the installation screen for the game.

---

### Post by Dapilot1 on 2007-11-04
Sweet! I believe you found the answer. I'm installing it now.

---

### Post by Dapilot1 on 2007-11-04
Good News:
I got the game installed.
Sound works.

Bad News:
I can't see most of the stuff until I touch it.
*I see buildings insides, but when I hit the wall the wall will appear.
*The human guys don't show up at all.
*The vehicles don't show up at all.

Not quite sure whm, but it is probably because I am running it on a Radeon 9800 XT with only 512 mb of ram.

---

### Post by ZERO_SHIFT on 2007-11-19
upgrade?

---

### Post by Dapilot1 on 2007-11-25
Not going to bother, I'm saving to get one of those Dell Ubuntu laptops before I go to college.

---

