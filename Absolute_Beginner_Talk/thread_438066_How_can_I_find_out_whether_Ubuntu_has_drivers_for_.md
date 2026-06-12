---
title: "How can I find out whether Ubuntu has drivers for my dial-up modem?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-09
Ubuntu "help" says it does not have drivers for most dial-up modems.  How can I tell whether Ubuntu has the
drivers for my laptop's modem or not? My modem is internal, linked on the motherboard.

My laptop modem: MINI PCI type 3B Data Fax Modem by 3COM. 
                               copyright 1997 by 3COM corp. 
                               File Version 2.19.012.0028
                               Port: Com 2
                               IRQ 9
                               Connection Preferences: Data Bits 8
                                                                        Parity none
                                                                        Stop Bits 1

---

### Post by Kobalt on 2007-05-09
Have you tried this : [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) ?

---

### Post by WNDS1701 on 2007-05-09
Hello,


try [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

There you will find a lot of hardware lists and probably even your modem. As it is a 3COM it should be well recognized in Ubuntu.


Good luck!

---

### Post by Bachstelze on 2007-05-09
Run the scanModem tool. It will generate a buch of text files, paste the ModemData.txt

---

### Post by swarup on 2007-05-09
> **HymnToLife said:**
> Run the scanModem tool. It will generate a buch of text files, paste the ModemData.txt

The reply just before yours told me to go to a website to see if my modem is listed on supported hardware. I went there, and the only modem that was listed was "Sagem Fast 800 Modem". So I presume my modem is not supported.

That brings me to your point about scanModem. That is the next question I was going to ask-- because I've already downloaded scanModem and I have it in my computer. I put it, as they said to, in the c:/temp folder of my Windows 98. So now I need to bring it into Ubuntu 7.04 and run it. --That is totally beyond me. They gave instructions as to how to do it, but I do not understand about command lines. I tried writing the lines in the "terminal" application, but it rejected them.

Here is more detail:

Assuming that Ubuntu does not have the drivers for my modem, the Ubuntu wants
me to find out the "chip set" of the modem. Ubuntu says, it needs that so I can then find
out what driver it needs. To find out the "chip set", Ubuntu recommended
I download a program called "scanModem"-- which I did download. They said
I could put it in my Windows 98, in the C:\temp folder. I did that. But then, Ubuntu
gave me around 4-5 lines of commands that they want me to type in in Ubuntu. I tried
writing them in in the "terminal" application, but it rejected the lines.
This is something I am entirely unfamiliar with, and I neither know what the command
lines mean, nor do I know how to use them.

Here are the command lines:

ls/mnt        (they say this line is to see the path to my Windows disk)
cp/mnt/msdos/temp/scanModem.gz.
gunzip scanModem.gz
chmod +x scanModem
sudo ./scabModem

Please let me know how to use all this. (That is, assuming Ubuntu in fact does not
have the driver for my modem.)

Also, what is the system according to which files are listed and arranged in Ubuntu?
I wanted to take the scanModem program and paste it into Ubuntu myself, but I could
not understand the pathway "mnt/msdos/temp". They said that the "."
at the end of that line is to put the file in the "current directory" 
-- but I do not know where that is either....

---

### Post by Bachstelze on 2007-05-09
This assumes you mounter your Windows partition on /mnt/msdos. You basicaly just need to copy the file in your Ubuntu installation, using an USB stick for example, or directly from the Windows partition if you're dual booting. I'm at school right now so I can't help you more, I'll give you more details if you need them when I'll be back home.

---

### Post by swarup on 2007-05-09
> **HymnToLife said:**
> This assumes you mounter your Windows partition on /mnt/msdos. You basicaly just need to copy the file in your Ubuntu installation, using an USB stick for example, or directly from the Windows partition if you're dual booting. I'm at school right now so I can't help you more, I'll give you more details if you need them when I'll be back home.

That would be great, if you will send me more details later. Because I don't even understand where to copy the file in my Ubuntu installation. (If this were Windows, I have a better idea. But being Ubuntu, I have no idea.) I will be deeply appreciative if you can send me more detailed instructions. If it is easier, you can simply e-mail them to me at <dinbandhu@sprynet.com>

Thanks!

---

### Post by girishv on 2007-05-09
Hi,

since you want to install modem on ubuntu and you can run scanmodem in windows, I assume that you are dual booting. Here are the two ways you can copy the scanmodem.gz file into ubuntu.

1. If you are dual booting
Find out on which partition your windows is installed.
mount the partition in ubuntu (if it is not already mounted). Assuming your first partition where windows resides is /dev/sda1, do
sudo mkdir /windows (if it is not there)
sudo mount /dev/sda1 /windows
sudo cp /windows/temp/scanModem.gz . (or any other name you might have given to the output of scanmodem)
The above command will copy the file scanModem.gz to the current directory

And, continue with other instructions

In the second way, just copy the file in a USB (using normal method)

boot into ubuntu

copy the file from USB into one of the directories, say Desktop

open a terminal, chdir to the Desktop directory and continue with the instructions

Girish

---

### Post by swarup on 2007-05-09
> **girishv said:**
> Hi,

since you want to install modem on ubuntu and you can run scanmodem in windows, I assume that you are dual booting. Here are the two ways you can copy the scanmodem.gz file into ubuntu.

1. If you are dual booting
Find out on which partition your windows is installed.
mount the partition in ubuntu (if it is not already mounted). Assuming your first partition where windows resides is /dev/sda1, do
sudo mkdir /windows (if it is not there)
sudo mount /dev/sda1 /windows
sudo cp /windows/temp/scanModem.gz . (or any other name you might have given to the output of scanmodem)
The above command will copy the file scanModem.gz to the current directory

And, continue with other instructions

In the second way, just copy the file in a USB (using normal method)

boot into ubuntu

copy the file from USB into one of the directories, say Desktop

open a terminal, chdir to the Desktop directory and continue with the instructions

Girish


I do not know whether Windows is "mounted" in Ubuntu or not, perhaps because I do not understand just what "mounted" means here. It is a term I have seen in the last two days since I started researching Ubuntu, but I'm not quite clear on the meaning yet. This much I can say though-- the windows partition is fully visible in Ubuntu's nautilus file manager so I can see all the c:/   folders etc there. If that is what you mean. 

Then--and this is a critical point--I do not understand what you mean by  "do sudo mkdir /windows". Do you mean that I should open the "terminal" application and type this line there? Please confirm. And what does "sudo" mean? Is there a place where I can check to see what all these code words mean?

And then when you write, "And, continue with other instructions"-- does that mean that I should go on typing those other command lines which I mentioned in my previous posting, in the "terminal" application? Please clarify.

Whenever someone talks about writing a "command line", does that mean they are doing it in the "terminal" application?

---

### Post by NESFreak on 2007-05-09
maybe it's a stupid question, but have you tried the modem?
Did you get some error message?

---

### Post by swarup on 2007-05-09
> **NESFreak said:**
> maybe it's a stupid question, but have you tried the modem?
Did you get some error message?

Actually, it's not a stupid question. -- When I went to the Ubuntu 7.04 "help" file on connecting to the internet for dial-up modems, it didn't even say how to try the modem. It just said that ubuntu doesn't have the driver for most modems, and this is how to find out whether ubuntu has the driver or not. So how do I "try the modem"? I presume I need to create a dial algorithm just like one would do in windows. Where do you set that up ie put in the phone number and all that?

---

### Post by Bachstelze on 2007-05-09
There's absolutely no way a PCI "modem" would work "out of the box"...

---

### Post by swarup on 2007-05-09
I've already downloaded scanModem and I have it in my computer. I have a dual boot with Ubuntu 7.04 and Windows 98. I put the file, as they said to, in the c:/temp folder of my Windows 98. So now I need to bring it into Ubuntu 7.04 and run it. --That is totally beyond me. They gave instructions as to how to do it, but I do not understand about command lines. I tried writing the lines in the "terminal" application, but it rejected them.

Here is more detail:

Assuming that Ubuntu does not have the drivers for my modem, the Ubuntu wants
me to find out the "chip set" of the modem. Ubuntu says, it needs that so I can then find
out what driver it needs. To find out the "chip set", Ubuntu recommended
I download a program called "scanModem"-- which I did download. They said
I could put it in my Windows 98, in the C:\temp folder. I did that. But then, Ubuntu
gave me around 4-5 lines of commands that they want me to type in in Ubuntu. I tried
writing them in in the "terminal" application, but it rejected the lines.
This is something I am entirely unfamiliar with, and I neither know what the command
lines mean, nor do I know how to use them.

Here are the command lines:

ls/mnt (they say this line is to see the path to my Windows disk)
cp/mnt/msdos/temp/scanModem.gz.
gunzip scanModem.gz
chmod +x scanModem
sudo ./scabModem

Please let me know how to use all this. (That is, assuming Ubuntu in fact does not
have the driver for my modem.)

Also, what is the system according to which files are listed and arranged in Ubuntu?
I wanted to take the scanModem program and paste it into Ubuntu myself, but I could
not understand the pathway "mnt/msdos/temp". They said that the "."
at the end of that line is to put the file in the "current directory"
-- but I do not know where that is either....

---

### Post by Bachstelze on 2007-05-09
OK, so you're dual booting ans scanModem is on your Win partition, will be fairly easy to get it then. What does that command output ?

```
mount
```

---

### Post by swarup on 2007-05-09
> **HymnToLife said:**
> OK, so you're dual booting ans scanModem is on your Win partition, will be fairly easy to get it then. What does that command output ?

```
mount
```

I'm in the middle of transferring some files over from an external drive. It'll be done in 10 minutes--then I'll try that code and let you know.

---

### Post by Bachstelze on 2007-05-09
I'll be gone to bed by then, feel free to PM me to remind me about this thread if it gets lost.

---

### Post by swarup on 2007-05-09
I did the "mount" command. It gave me a long string of about 15 lines.

---

