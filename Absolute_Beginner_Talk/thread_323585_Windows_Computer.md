---
title: "Windows Computer"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-12-22
I have two computers one running windows and one running ubuntu and windows.  I primarily run ubuntu but keep my second computer for extra space and backup.  How can I access the second computer's files that is running windows on my ubuntu computer.

---

### Post by PriceChild on 2006-12-22
samba is is the way to cooperate with Windows environments. Links with more info: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) and [http://help.ubuntu.com/ubuntu/serverguide/C/windows-networking.html](http://help.ubuntu.com/ubuntu/serverguide/C/windows-networking.html) - Samba can be administered via the web with SWAT

---

### Post by gentlemanmasher on 2006-12-22
I really only want to access the windows files I don't need to have access to my ubuntu box from the windows.  Do I still need Samba.  Is there an easier fix for my needs?

---

### Post by dbbolton on 2006-12-22
well, you could back them up on a disc or flash drive.

---

### Post by gentlemanmasher on 2006-12-22
Nah I have 60g of data on my other computer, but your right that is easy.  Maybe I should re-phrase.  Is there any easier solution than setting up Samba to access my windows file from my ubuntu box.

---

### Post by djheadley on 2006-12-22
Can you move the windows hard drive to the Ubuntu box?

---

### Post by gentlemanmasher on 2006-12-22
I could but I want to keep the windows box there.  I use it for backup and I already have all my ubuntu hard drive spots used.

---

### Post by seijuro on 2006-12-22
you could set up openssh server on the ubuntu machine then use a program like winscp on the windows machine to transfer the files over. unless you want to specify a specific port you don't need to do any post install config for openssh. In winscp use your ubuntu box's username and password for the connection login info and set the protocol to ssh/sftp rather than ftp.

---

### Post by Spinelli on 2006-12-22
I think I have a very simple solution to your problem. I think the default Ubuntu installation comes with two programs that allow you to browse Windows shares on a network. smbclient is a command line tool. On my computer it is located in /usr/bin/smbclient. Nautilus, the default file manager in Ubuntu, should also allow you to browse Windows shares on the network. Clicking on Places>Network Servers should allow you to browse all Windows shares on your network. I am assuming that your Windows computer and your Ubuntu computer are networked. On your windows computer you need to simply set up file sharing. I am assuming you are using Windows XP. For more information about smbclient you should type the following at the command line ....

```
man smbclient
```

I could be completely wrong since I don't have any computers running Windows on my home network.

---

### Post by gentlemanmasher on 2006-12-22
all right question.  It allowed me into by windows computer once and I could browse files, now the second time I try and go in it says the location is not a folder.  I just brosed my files once, can anyone help.

---

### Post by gentlemanmasher on 2006-12-22
Just in case anyone wants to know.  I did manage to get it working.  I simply went to places>connect to server>Service type  windows share>  then in the server area I put in my windows box ip address.  

All is well.  

Thanks

---

