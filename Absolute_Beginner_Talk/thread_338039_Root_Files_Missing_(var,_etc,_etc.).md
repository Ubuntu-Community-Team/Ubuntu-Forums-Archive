---
title: "Root Files Missing (/var, /etc, etc.)"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by 4.9 on 2007-01-13
I installed Kubuntu onto my Ubuntu System through the terminal with Apt-get, and now all my root file system files have disappeared! All that is left is the media and home folders. The folders still exist, but are hidden. I tried sudo chmod 777 /var to fix it, but it didn't work. I think they may have been hidden by a glitch. Can someone give me a list of the filesystem folders and tell me a command to make them readable to me again? Like a chmod ### command. Btw, is there a virus in the Kubuntu Repository installation repository?

---

### Post by astoltz on 2007-01-13
I'm not sure I understand.  If /etc were really missing or renamed, Ubuntu would not boot.  Hidden files (and directories) in Linux start with a dot:  /etc is normal and /.etc is hidden.

I don't use KDE (Kubuntu) but is it the file manager that is just not showing these system files? 

Try opening a terminal and type: ```
cd /
ls
```Is everything there?

---

### Post by %hMa@?b&lt;C on 2007-01-13
> **astoltz said:**
> I'm not sure I understand.  If /etc were really missing or renamed, Ubuntu would not boot.  Hidden files (and directories) in Linux start with a dot:  /etc is normal and /.etc is hidden.

I don't use KDE (Kubuntu) but is it the file manager that is just not showing these system files? 

Try opening a terminal and type: ```
cd /
ls
```Is everything there?
konqueror just hides all but /media and /home to prevent you from doing anything stupid. dont worry, all files are still there:rolleyes:

---

### Post by 4.9 on 2007-01-13
Yeah.

---

### Post by 4.9 on 2007-01-13
> **jeffc313 said:**
> konqueror just hides all but /media and /home to prevent you from doing anything stupid. dont worry, all files are still there:rolleyes:

I'm on the Gnome part of my comp, and the only thing there is home and media.

What is the chmod command to make the files visible to me again?

---

### Post by ButteBlues on 2007-01-13
> **4.9 said:**
> I'm on the Gnome part of my comp, and the only thing there is home and media.

What is the chmod command to make the files visible to me again?
Just hit CTRL+H.

---

### Post by %hMa@?b&lt;C on 2007-01-13
> **4.9 said:**
> I'm on the Gnome part of my comp, and the only thing there is home and media.

What is the chmod command to make the files visible to me again?
chmod READ WRITE EXECUTE
if you so, 755 should be what you want
sudo chmod 755 /

---

### Post by ComplexNumber on 2007-01-13
> **jeffc313 said:**
> chmod READ WRITE EXECUTE
if you so, 755 should be what you want
sudo chmod 755 /
root and some others need to be different though. the screenshot is a printout of "ls -l" on my system. root needs to be 555 instead of 755.

---

### Post by astoltz on 2007-01-14
The mode of the files (chmod is short for change mode) has nothing to do with whether they are visible.  In fact, you could hurt the system if you change them. List the files from a terminal - if they show up there, it is a setting in Konqueror (KDE) or Nautilus (gnome) that is hiding these files and there is nothing wrong with the system.

---

### Post by contadinoste on 2007-01-21
Yes, it's a new security feature of edgy in Konqueror ( maybe also in Nautilus). Open "root folder" tab and activate "show hidden files" then you will see them in the main window, but still not in the tree. Or type in konsole:
cd /
ls
Edit/Delete Message

---

