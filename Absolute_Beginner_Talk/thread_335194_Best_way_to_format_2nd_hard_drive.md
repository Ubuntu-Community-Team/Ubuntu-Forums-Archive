---
title: "Best way to format 2nd hard drive"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by capitaldigit on 2007-01-10
Hello all...I am a brand spanking new Linux user.  I've been around computers for years, vendor certified and all, but only in Windows products.  So this is a big (and sometimes terrifying) leap for me.  I have a 2nd computer that I have installed Ubuntu on.  I have a home network of XP machines, and would like to set up a 2nd hard drive in my Ubuntu box for mp3 storage.  I would like to be able to connect to this box from all other computers to access these mp3 files.  So here is my question...

1.  What would be the best file system to install on the mp3 drive so that Windows and Linux boxes can access it?  The 2nd drive has been installed, and is recognized through Administration-->Disks.

---

### Post by lucky_chouhan on 2007-01-10
Create 4 partitions  -


root
home
swap
then ntfs

and install ubuntu it automatically detect your ntfs partitions.

your 2nd question is your mp3 so if ubuntu you need to manually install codecs which play your mp3 and other audio files.


your just put 3 command in terminal and play all your audio and video files.:) 


1. sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base 

2. sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse 

3. sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

even i am play my audio and video via LAN without vlc.

for DVD Play - 

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

---

### Post by Coelocanth on 2007-01-10
Well, Windows and Linux can both read and write to FAT32, so that's probably the simplest way to go. I imagine there may be other choices, but that's probably easiest.

---

### Post by cult hero on 2007-01-10
If you don't mind installing 3rd party utilities on a Windows machine, they can be set up to read ex2fs/ex3fs. For external drives that I swap between Windows, Macs, Linux and BSD boxes (I work in a weird place) I just used FAT32 since everyone can read and write to it with no real issue.

I trust ex2fs on Windows far more than I trust NTFS writing on Linux. (And I'm not knocking Linux, but ex2fs is open and NTFS ain't. That's all.) However, if Linux doesn't need to write to the partition, NTFS works fine.

Rereading your post though, it seems to me that you want to, more or less, use your Ubuntu machine and have other machines in your house like a file server. If that's the case then the filesystem matters only to the local machine because it'll serve them up over the network via samba (the open version of Windows style file sharing). Use ex3fs on the the Ubuntu machine.

The only two times a filesystem really needs to be read/written to by multiple OSes is when you're in a dual boot environment and both OSes are sharing the same physical drives. The other instance is if you have an external drive that needs to be read and written to by multiple OSes (or even something like a pocket USB drive or something, once again I use FAT32 for those).

If machines are accessing information over a network, the filesystem is generally irrelevant. You don't need compatible filesystems when you FTP, do you?

(And I hope I haven't misread this and just talked on and on about something that didn't need to be covered. Better safe than sorry though!)

---

