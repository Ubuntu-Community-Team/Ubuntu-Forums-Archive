---
title: "dualboot ubuntu and xp doent work"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by waxfactor2nd on 2006-09-30
this is from the post: [http://ubuntuforums.org/showthread.php?t=268837](http://ubuntuforums.org/showthread.php?t=268837) but i was a dead end so i want help...

hi ive never used linux before, but everyone have to start at one point. ive chosen ubuntu to try, but i want to dual boot with windows xp. ive done as ive been guided, first installed windows xp on hdd 0 partition 1, then ive taken ubuntu and taken use the largest continuous free space and installed it. there where no problems. but when i now reboot my computer,it says grub loader 1.5
grub loading
grub error 22

before i can choose windows or linux.. now i dont know what i shall do.. can someone help me. im trying to install ubuntu 6.06lts for pc, and i have a amd atlhon 64 3700+, a8n-sli premium, 2gb ram, and two 250gb spinpoints (sata) (both linux and windows have to go on the first one.)

how shall i do??

ive tried as they say in the link to write:
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda? /mnt/ubuntu
but that i didnt understand but i didnt work after i wrote it...

when i write the command gksudo gedit /boot/grub/menu.lst it gives me this error: (gedit:8005): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ubuntu@ubuntu:~$
 and opens an empty gedit document.
when i write sudo fdisk -l i can see that where windows is its called: /dev/sda1
and linux is a /dev/sda2. but i dont know what i shall use this info for. so i havnt done anything with it / i guessed that there should stand the same thing as in the gedit doc but it didnt.. 

then bulldog says With this info you can alter GRUB [menu.lst] to correct the problems there seem to be. but i dont know what the word alter means but i gues it is change. but i dont know what to write into the menu.lst. so thats a dead end to..

and then he says if im in a live session (i gues that is when im using a livd cd / and that i am because the other thing doent work.) i can write sudo grub / then it says that it is probbing. but after a while i blinks as he says grub> and i can now write the next line wich is find /boot/grub/stage1 then i get (hd0,1) and he says i have to use that in the next line so i do (but later he says something about that i have a sata hdd and then it aint hd but sd or something like that. but it said hd) well i write root (hd0,1) and it works with no problem ( i tried with sd insted of hd but then i got error 23). then he says i have to write setup (hd0) so that i do and it dont say any problem. (i also tried to write hd0.1 and sda2 there but then i get an error. then he tells me to write quit to stop the grub>. and it does. but now i still get the f****** grub error22. wtf is wrong??

or here is what the error says::

 Originally Posted by waxfactor2nd
when i write find /boot/grub/stage1 i get (hd0,1) not sd, when i write root (sd0,1) i get error 23> error while parsing number...
if i write root (hd0.1) it sais filesystem type is ext2fs, paartition type 0x83
.then i write setup (sd0) it says eroor 23. but if i say hd0 it says: Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.



anyone who can help me???

---

### Post by harry555 on 2006-10-01
If you have nothing vital on your windows partition doing a new install of windows might be easier.   Boot up with XP Cd and delete all the partitions on the hd.  Then create a new partition using about half your hard drive.
Install windows on that partition.  Check that XP is working ok.  

Then install ubuntu again using the non-partitioned space on the drive.   From reading your post it seems that your whole drive is assigned to XP.  It could be that ubuntu will install easier if you try to put it onto non-partioned space.   I have had more success trying out distros doing it that way.

I am a linux newbie who has tried lots of diff. distros.   And my XP knowledge is slightly better!

(Go with Bulldog's advice his advice is far more knowledgable and less drastic than my idea.)

---

### Post by bulldog on 2006-10-01
Will try one more time but you have to read carefully and understand,not blindley copy/paste and think it's allright cause it isn't.

Your GRUb has not the proper entry's to boot,how this can happen I don't know.
What I do know is we can set this right but you have to cooperate and do a little thinking by yourself.
Thinking your a newbie and I can take care of everything isn't enough you have to do something by yourself.

Okay we have the output of fdisk.
Your Windows is sda1 and ubuntu is sda2 both on hd0 correct?
Now we are going to install GRUB again on hd0.

First boot into a live cd session and open a terminal and type the following command's one by one.
Now comes the hardest part after you gave a command you get a reaction in your terminal,now I want you to copy that reaction exactly as it is in the next command that you gonna give.
If you do that there shouldn't be any trouble.
Just do so no more no less.

```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1   /example (hd0,1)
```

This will return a location. 
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?) <----there the outcome of first command 
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

Now reboot and see if your problems are over.
If not,boot into the live cd again and we continue.

---

