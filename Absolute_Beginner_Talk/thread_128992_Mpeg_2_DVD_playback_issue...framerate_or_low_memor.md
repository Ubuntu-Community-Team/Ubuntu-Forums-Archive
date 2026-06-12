---
title: "Mpeg 2 DVD playback issue...framerate or low memory?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-02-12
I finally got my Mpeg-2 DVD's to play, using gxine, which I find great, and the only player that works on my 64bit install. The only problem is that it is if my system cant handle the playback, even in the smallest window without blurred slow framerateish playback....like my system cant handle it.

I'm using an MSI mobo with built in ATI video set to VESA + 128mb(shared of 512 system), using sudo dpkg-reconfigure xserver-xorg. Is there a way to make my playback more robust? It doesnt take much to have smooth playback, I should be able to handle it. Maybe reconfigure with 256mb? Any ideas or help? Thanks

---

### Post by noigeaR on 2006-02-12
it's probably the dma mode that isn't turned on for your dvd drive.
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by gordong11 on 2006-02-12
[QUOTE=noigeaR]it's probably the dma mode that isn't turned on for your dvd drive.
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)[/QUOTE]
Enabling DMA

To enable DMA, you need to use the hdparm command and the configuration file hdparm.conf.

These instructions assume that you are trying to enable DMA on hdc, usually the CD-rom drive.

   1.  See the what the settings are on /dev/hdc
          *
    
   

   2.      If you get a line like  using_dma    =  1 (on), DMA is already enabled. Skip to step 4 to see if it has been enabled at boot time.
   3.      Enable DMA on /dev/hdc
          *

   sudo hdparm -d1 /dev/hdc
   

   4.      You have now enabled DMA for the drive. However, in order for the settings to be automatically applied at boot there you need to edit the /etc/hdparm.conf} script. To do this use this command: sudo gedit /etc/hdparm.conf

Add the following to the end of your hdparm.conf

       /dev/hdc {
   dma = on
   }

OK, thank you!!  i TRIED STEPS 2-4, and if I do STEP 1: I GET "NO SUCH FILE/DIRECTORY ERROR, BUT ASKS ME FOR PASSWORD.
(possibly hdc is not my DVD-Rom drive?)

 DID I DO SOMETHING WRONG? i DID REBOOT. POSSIBLY I ADDED THE /DEV/HDC WRONG AT THE END OF THE SCRIPT?(I SKIPPED A LINE BEFORE ADDING,BUT THAT SEEMED THE WAY). SHOULDN'T I STILL BE ABLE TO PULL UP sudo hdparm /dev/hdc? IS THERE ANOTHER WAY? THANKS

---

### Post by gordong11 on 2006-02-12
Any ideas?

---

### Post by noigeaR on 2006-02-13
seems like your dvd drive isn't at /dev/hdc/
put a cd or dvd in your drive and mount it so that you can access it in nautilus or konqueror. then open a console and type the command **df** and press enter.
this should give you a list of the drives in your computer. one of the lines (probably the last) should have an entry with /dev/cdrom or /media/cdrom0 at the end. for my computer it looks like this

/dev/hdc               4416256   4416256         0 100% /media/cdrom0

the /dev/hdc at the beginning of the line is the device name of my dvd drive. if this isn't /dev/hdc for you, then replace every occurrence of /dev/hdc in the how-to from the wiki with the name it shows for you (probably /dev/hdb or /dev/hdd, if you have a scsi or serial ata drive, then it might be /dev/sdb or something like that).

---

