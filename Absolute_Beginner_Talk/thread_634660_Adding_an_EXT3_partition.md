---
title: "Adding an EXT3 partition"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by 1967tempest on 2007-12-07
Hello all:
      I am a noob at the Linux thing.  I am trying to make the SWAP.  I love that most of the stuff that you would pay for is FREE.  Plus with 4 CPU's this thing SMOKES.  I hav my Ubuntu on a SCSI drive.  I just formated the IDE 40gb drive I have in Gparted.  Now I can see it but I cant do anything.  If I can do anything after reboot it goes back to nothing.  I also have a 73gb SCSI drive with all of the music on it.  I need two things.  And I am sorry to say that I had learned Winblows so I need step by step instructions.  Lets put it this way, "In Linux, I know enough to be mildly dangerous."

1: I need to permanently mount the IDE drive formatted as EXT3.
2 I need to permanently  mount the SCSI drive.  I have run ntfs configuration tool, but every time I reboot, it asks for password to add the drive.  Just annoying.  I have to mount the drive, then start my MP3 player...

Anyway, thanks for the help.  I live the little stuff in Ubuntu that Winblows doesn't have.

Thank you all,
Dave

---

### Post by rexxxlo on 2007-12-07
i have just dealt with this the hardway so i can do it now 

if you used gparted and formatted the drive and youjust need to mount it 

first you need to decide where to mount it  

i am assuming that the scsi drive that has your music on it will go in

 /home/music

and the other can go in 

/storge

then in a terminal

> gksudo gedit /etc/fstab


and there you can add the 

results you find from this code
> gksudo gedit /etc/fstab

it will tell you the size and name of the drive,for instance my drive is
/dev/sda1 /storage ext3 defaults 0 2

your will be named something different  just add that line with the name of your drive to the line and save it 

then
> sudo chown -R lolo:lolo /storage
the lolo is my user name replace it with yours 
then in the terminal again 

> sudo mount -a

that should do the trick i think i might have missed something but imnewat this too just about a few weeks

---

