---
title: "CDRW Won't Mount"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by E.T.Expatriate on 2007-08-26
I just installed Wine, and thought I'd try installing some old Windows games. However, I couldn't get the CD drive to mount. Okay, I figured, I just don't know how to get the system to read a Win disc yet; try again later. But then I tried to read a Ubuntu disc, and that didn't mount either. I restarted the system, and I still can't mount discs.

The particulars:

The CDRW drive opens and closes fine, but Ubuntu doesn't automatically mount an inserted disc.

Trying to mount it through the browser gives this message: "Unable to Mount the Selected Volume. (show more details: mount: special device /dev/scd0 does not exist)".

Going to terminal and entering  "mount /media/cdrom" gives me "mount: special device /dev/scd0 does not exist".

So what am I missing?

---

### Post by schorsch on 2007-08-26
What is the output of
```
lshw -C disk
```

---

### Post by E.T.Expatriate on 2007-08-26
*-disk                  
       description: SCSI Disk
       product: WDC WD400EB-75CP
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 06.0
       serial: WD-WMAATJ866697
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 36GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          size: 1098MB
          capacity: 1098MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 1098MB
             capabilities: nofs

---

### Post by schorsch on 2007-08-26
Hmmm ... your CD-RW isn't detected. Pretty weird as you installed the OS via CD, right? Have you already installed all updates? Which type is your CDRW: SCSI, USB, IDE ...? Sorry, right at the moment I have no idea what causes your problem ...

---

### Post by E.T.Expatriate on 2007-08-26
> **schorsch said:**
> Hmmm ... your CD-RW isn't detected. Pretty weird as you installed the OS via CD, right?
Yes, very recently to, within the last week.
> Have you already installed all updates? Which type is your CDRW: SCSI, USB, IDE ...?
I'm afraid I'm not familiar with those terms. Where would I find that info? Its a Dell budget-machine standard CDRW from 2004, if that helps.

---

### Post by schorsch on 2007-08-26
Well you can try to update your whole system to an actual state:
```
sudo apt-get update
sudo apt-get upgrade
```
After the last command you will see how many updates will be installed and you can stop the process by typing "n". Are there any updates available to your system?

---

### Post by init1 on 2007-08-26
```

sudo mount /dev/sda /mnt
ls /mnt

```

---

### Post by E.T.Expatriate on 2007-08-28
> **schorsch said:**
> Well you can try to update your whole system to an actual state:
I update the sysytem whenever prompted to do so. Funny thing is, on some boot-ups, the system dose recognize the CDRW and it works fine. Other times, no. It seems entirely random.

EDIT: And I just ran the command line update method you gave. No dice.

---

