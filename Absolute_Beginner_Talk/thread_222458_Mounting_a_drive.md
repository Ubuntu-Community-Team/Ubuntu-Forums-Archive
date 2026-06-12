---
title: "Mounting a drive"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by davidY on 2006-07-25
How do i mount a partition so that i can write to it? I have tried, but while I can mount it, it is always read only. I have a ext3 partition on the hdd. I am mounting it currently to /media/documents

---

### Post by steve.horsley on 2006-07-25
How are you mounting it? Manually, or is it mounted at startup. The startup mounting is controlled by a file called /etc/fstab so it might help to post that.

But it is probably just a permissions thing. Ext3 stores permissions flags so you may not have permission even if the drive is mounted read-write. Have you tried using root privilege to write to it? You can use a command **gksudo nautilus** that gives you a nautilus file manager window with full access rights - try that.

---

### Post by richbarna on 2006-07-25
you have to open the terminal and type these commands:-
> sudo chown -R rich:rich /media/documents
(where my user name is "rich")
then:-
>  sudo chmod -R 755 /media/documents

---

### Post by richbarna on 2006-07-25
To make sure the partition is in fstab, and mounts at boot :-
> sudo cp /etc/fstab /etc/fstab_backup
>  gksudo gedit /etc/fstab

You need to add this line (with your hardrive/partition hda ?,?
> /dev/hda? /media ext3 defaults 0 0
I am assuming that documents is only a file inside the /media partition.

Save the file and exit. Then mount the partition:-
> sudo mount -a

---

### Post by davidY on 2006-07-25
Uh.. it still does not let me write to it

---

### Post by davidY on 2006-07-25
i try to save a text file to it, and it sort of pauses while saving the file

---

### Post by aysiu on 2006-07-25
Do post #4 and *then* post #3.

---

### Post by davidY on 2006-07-25
Ok, ths is wierd. now tha i check, the file is there. It seems like the computer just lagged for a sec ^^....

oh it is all ok

i thnk the file explorer lagged for a moment and did not know the drive was "my precious..."

thanks!! it is all fixed

---

### Post by richbarna on 2006-07-25
> **davidY said:**
> 

thanks!! it is all fixed

Cool :)

---

