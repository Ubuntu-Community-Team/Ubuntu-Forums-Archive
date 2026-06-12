---
title: "[SOLVED] Go back to Windows without a CD or cloppy drive"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by ebrewer27 on 2008-01-02
Ok, so bear with me on the long-winded explanation, but I feel it's better to give you too much info than too little:

I've been a Windows user for a long time (nothing against Linux, just didn't spend the time to get into it). I have an old Sony PCG-SRX99P laptop, which is an "ultra-portable", i.e., no built-in CD or floppy drive. I used to have a firewire-type external optical drive from which I could boot install disks and such, but that burned out on me and it's hard to find a replacement.

Not such a big deal as I could share the optical drive from my home desktop over my personal network, but then the hard drive on my laptop died and I was stuck with no way of reinstalling Windows (except for PXE, which I tried, but all of the instructions I found on the web for doing so were too cryptic and time-consuming).

So, of course I snooped around and found that it was much easier to install Ubuntu using PXE, which I did, and I have to say that it's an amazing OS.

However, I've had to make the hard decision of switching back to XP. As I said, Ubuntu and Linux in general is great, but for the things I need my laptop (using it for work, playing certain games, etc.), and being that I have a busy life and young children, I simply don't have the time right now to learn how to work with Ubuntu. (Plus, I have a wife who is not as technically-minded, who shares the laptop with me, and who has turned on her nagging function for me to put Windows back on).

So, my problem is again that I cannot use the Windows CD to boot the laptop and install XP. I have instead created a separate FAT32 partition and copied the contents of the XP install CD there. My theory is that I should be able to tell the system to boot that partition instead of Ubuntu, thus running the XP install and solving my problem. However, despite all of my snooping around the web, I cannot find how to do this.

I'm using a single 120 gig hard drive, with one ext3 root partition (/dev/sda1), one ext3 home partition (/dev/sda3), one swap partition (sda2), and, as I mentioned, one fat32 partition containing the contents of the XP install CD (sda4).

I appreciate your excusing my newbie-ness and helping me out with this. If the information is clearly posted elsewhere and I've missed it, I apologize.

---

### Post by Delvien on 2008-01-02
This might be the wrong place to ask. I'm not quite sure how to help you, but... you might try seeing if there is a way to install XP from a thumb drive? that PC i believe supports bootable USB? 

I'd try that.. otherwise sorry I cant help more.

---

### Post by foolsh on 2008-01-02
the instructions for installing ubuntu with PXE should be able to boot the windows install disc I think thats a better method than trying what you said
shouldn't you be able mount an iso of the windows install cd on the pxe server and then piont the pxe daemon to the path you mounted it in and have the pxe clients boot from that.
Im no expert by far, its just that if you boot ubutnu with pxe you should be able to boot any OS

---

### Post by Linuxratty on 2008-01-02
Ok,I could be off base here,but you installed Ubuntu first and then tried to install Windows?
 You need to do it the other way around...Install Windows first,then Ubuntu.

---

### Post by ebrewer27 on 2008-01-07
I finally figured it out, and here's how:

You'll need 2 computers on your home network: The one on which you want to install Windows, and another to act as a server. We'll call them client and server, respectively.

1. Take your WinXP cd and copy the I386 folder to the server pc. Share this folder on the network (right-click->Properties->Sharing).

2. Follow this link: [http://thesystemadministrator.com/The_System_Administrator/Tips_&_Tricks/PXE,_aka_Pre-Execution_Environment_-_Part_1/]("http://thesystemadministrator.com/The_System_Administrator/Tips_&_Tricks/PXE,_aka_Pre-Execution_Environment_-_Part_1/")

3. Download all of the files he mentions. Create a folder on your server pc  called "PXEServer" and network-share this drive. Then, extract the files mentioned on the web page to the respective subfolders. Extract the netboot and Win98 boot image ("DOS bootable floppy" as he calls it) to the folder "C:\PXEServer\TFTPRoot\"

4. Follow the steps on that web page exactly as they are laid out. When configuring the TFTPD32 program (on the "DHCP server" tab), the parameters are as follows:
"IP Pool starting address" - Just pick the starting IP that your network assigns to PC's connected to it (usually 192.168.0.100 or 192.168.1.100)
"Size of Pool" - 10 is fine
"Boot file" - pxelinux.0
"WINS/DNS Server" - the IP of your router (usually 192.168.0.1 or 192.168.1.1)
"Default router" - again, the IP of your router
"Mask" - usually 255.255.255.0, unless you've configured your network in a different way.

5. Make sure that "Current Directory" is set to the location of the pxelinux.0 file.

6. Connect your client pc to the network, boot it up, and enter the BIOS. Look for the option that lets you turn on "network boot", and set the boot priority so that network booting takes place before the hard drive. Save and exit.

7. If everything was set up correctly, your client pc should boot into a menu asking you which image you would like to load. Select the netboot option (or whatever it's called - you don't want the "clean win98" option").

8. Once that has loaded, you will be at a good old-fashioned DOS prompt. Now, if you have not already done so, you will first need to partition your hard drive so that Windows can install correctly. This is done with the FDISK command. If you need help using this command, type it in with the /? option, or Google it. Basically, you want to delete all partitions and create a new FAT32 partition (or however else you want to partition the drive). There is also an option with FDISK to repair your master boot record. You want to use this if Linux was previously installed on that computer.

9. You will next have to use the "net use" command to map the shared I386 folder that is on your server pc. It goes something like this:
"net use d: \\computer name\shared folder"
(you can use the "net use /?" command to get the exact syntax)

10. Once this is done, you should be able to change to that drive letter and have access to the I386 folder. If so, run the "winnt.exe" program. This will start the Windows install program. It will take a little bit of time, as it has to first copy a bunch of setup files to the client pc, but once it finishes, you'll have a fully-functional WinXP box.

11. At this point, I would recommend creating a separate "recovery" partition on your client computer, one on which you will put the contents of your WinXP install CD, and adding an entry for this partition to your Windows startup. This way, if you ever need to reinstall Windows, you can then do it from just the one computer, instead of having to mess with the whole PXE process again.

Let me know if you have any questions or problems.

---

### Post by foolsh on 2008-01-07
thats what I had in mind Good show!
Welcome newcomer I think we're gonna like having you here at the Ubuntu Forums.

---

