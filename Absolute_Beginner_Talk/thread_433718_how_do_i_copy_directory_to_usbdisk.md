---
title: "how do i copy directory to usbdisk"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-05-05
Hi I want to copy a cirectory namely /etc/ppp to a usb disk but am not sure of the exact command to type. I saw a post that said to do this: sudo cp /ol_location/ /new_location but it didn't work for me. So what I typed was: sudo cp /etc/ppp/ /media/usbdisk .

---

### Post by Rospo Zoppo on 2007-05-05
Maybe the disk is NTFS and you don't have the drivers..

---

### Post by orange2k on 2007-05-05
Can`t you just copy & paste in the nautilus?

---

### Post by trak87 on 2007-05-05
Make sure your usb disk is mounted before copying something to it. Go to Places, Computer, and look for your usb device there. Right click on it and select mount (if it's not already mounted). At that point you can copy stuff to it (provided the usb disk is not formatted in the ntfs file system).

---

### Post by rapattack1 on 2007-05-06
I do not know what ntfs really is but the usbflash thing mounts automatically so there is no worries there. I cannot copy and paste. i need to be root to do this.

---

### Post by Rospo Zoppo on 2007-05-06
To be root type in a terminal 
sudo nautilus 
and then go to the hard drive.. If you cannot write even in this case you must install ntfs driver..

---

### Post by rapattack1 on 2007-05-06
Thanks I was able to navigate to the right folder but I still got the error that you will see in the attachment. I got the folder and some of the contents but it denied me pap-secrets. I need that one.

---

### Post by drowner on 2007-05-06
seems odd.

if you sudo nautilus it, i cant for the life of me imagine the problem

(LOL @ being unhelpful)

---

### Post by rapattack1 on 2007-05-06
He he don't worry. I just spoke to a friend on the cell phone and he said that I might have to do : sudo daeman or something like that? I will post what he says tomorrow as he is out on the town having fun. He wanted to escape his home network as he felt ](*,) ](*,) :confused: :-k

---

