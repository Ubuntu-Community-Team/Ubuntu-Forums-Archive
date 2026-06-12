---
title: "Install Applications on non-networked computer"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Tobysan on 2006-11-14
How can I download other applications onto a pc that is not connected to the internet or a network?

---

### Post by aysiu on 2006-11-14
Is your PC that *does* have a connection able to run a  Ubuntu Desktop CD?

---

### Post by bswilson on 2006-11-14
> **Tobysan said:**
> How can I download other applications onto a pc that is not connected to the internet or a network?

You can't.  The word *download* means to obtain an item from a remote networked source, dude.

---

### Post by Max_Might on 2006-11-14
You can`t download them but you can install them if you have the .deb packages on your PC.

---

### Post by aysiu on 2006-11-14
> **bswilson said:**
> You can't.  The word *download* means to obtain an item from a remote networked source, dude.
You have a point there.

I guess I was assuming the OP meant *install* instead of *download*.

---

### Post by Tobysan on 2006-11-14
Can I install applications and extentions by down loading to a disk and installing onto another pc. If so, how?

---

### Post by aysiu on 2006-11-14
> **Tobysan said:**
> Can I install applications and extentions by down loading to a disk and installing onto another pc. If so, how?
Do you have a networked PC that can run the Ubuntu Desktop CD (and on which the Desktop CD detects the network connection)?

P.S. Don't double-post. I've merged your two threads.

---

### Post by Tobysan on 2006-11-14
Yes. My pc at the office can do all the downloads. I just need to get them onto my pc at home which has no connection.

---

### Post by aysiu on 2006-11-14
This is what you should do, then (these instructions assume you have at least 256 MB of RAM on your networked computer--512 MB or more would be ideal).

1. Boot up the Ubuntu Desktop CD on your networked computer.

2. Clean out the /var/cache/apt/archives folder with this [terminal](http://www.psychocats.net/ubuntu/terminal) command: ```
sudo aptitude clean
```

3. Go to Synaptic Package Manager and install whatever you want to install on the other computer.

4. Copy the contents of /var/cache/apt/archives to a USB stick or some other removable drive.

5. Copy the contents from the USB stick or drive to the desktop of your non-networked computer

6. Paste these commands in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

If you have less than 256 MB of RAM or plan to install *a lot* of programs, the instructions get a bit more complicated.

---

### Post by Tobysan on 2006-11-14
Thank you v much and good night. I'll try in the morning. Chers

---

### Post by aysiu on 2006-11-14
You may also want to look into Ubuntu Plus:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

---

