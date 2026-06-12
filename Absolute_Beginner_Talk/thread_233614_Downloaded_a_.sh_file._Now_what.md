---
title: "Downloaded a .sh file. Now what??"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Robert Leithe on 2006-08-10
I have one program I can't live without (to be fair, I can LIVE without it, but I'd have to change my job...) so I wanted to try the Crossover Standard software and see if it couldn't run this program for me.

I'm all new to Linux, and is currently running Ubuntu 6.06 LTS.

I downloaded a file called install-crossover-standard-demo-5.0.3.sh
And there I am. Sitting here, looking at this file. Wondering what I'm gonna do with it, in order to get a working install of Crossover.

Any suggestions from the pros?

Sincerely
Robert Leithe

---

### Post by tseliot on 2006-08-10
Moved to a more appropriate section

---

### Post by davebgimp on 2006-08-10
Looks like a shell script.

Open a terminal and navigate to where the script is and type:

**chmod 755 install-crossover-standard-demo-5.0.3.sh**

and then

**sudo ./install-crossover-standard-demo-5.0.3.sh**

---

### Post by Robert Leithe on 2006-08-10
First: I'll doublecheck where I put my postings in the future.

Then: I'm getting this message:
The '/home/robert' directory does not belong to you.
Point $HOME to your home directory and try again.

The file is located at /tmp

---

### Post by givré on 2006-08-10
Don't run it with sudo, try that :
```
./install-crossover-standard-demo-5.0.3.sh
```

---

### Post by MaximB on 2006-08-10
well - the problem is that the tmp folder is located in root
so you can try to login as a root
meaning : in the terminal type "su" then your password hit enter
and then do the command
or try to move your file from the tmp folder to your home directory
you can do this by running nautilus as a root
terminal : "su nautilus"

hope it helps

---

### Post by givré on 2006-08-10
No the problem is 'The '/home/robert' directory does not belong to you.' ie /home/robert belongs to robert but you run the script as root...
Try to run as simple user and see what's happens.

---

### Post by Robert Leithe on 2006-08-10
> **givré said:**
> Don't run it with sudo, try that :
```
./install-crossover-standard-demo-5.0.3.sh
```

This worked just fine, thanks! :)

Crossover didn't run my Windows software, though. As it turns out it requires IE. Guess I'll be looking for another job...:-x

---

### Post by mostwanted on 2006-08-10
> **Robert Leithe said:**
> This worked just fine, thanks! :)

Crossover didn't run my Windows software, though. As it turns out it requires IE. Guess I'll be looking for another job...:-x

Why don't you install IE and then try re-installing?

---

### Post by qrm on 2006-08-10
i guess yóu could install IE too with crossover and check what happens then

---

### Post by Robert Leithe on 2006-08-11
I installed IE6, but when CrossOver initiate the install of the other piece of Windows software it (the installer for this other software) still keeps telling me that I need IE. So evidently CrossOver can't "tell" this software that IE is already installed.

---

### Post by diepruis on 2006-08-11
Could you try installing IE and the software under wine? Not sure if this will change anything, but it's worth a try...

---

