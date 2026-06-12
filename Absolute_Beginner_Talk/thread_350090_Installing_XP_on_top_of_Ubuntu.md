---
title: "Installing XP on top of Ubuntu"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Unterseeboot_234 on 2007-01-31
Hate to say this, but I've **got** to install XP and here's the reason. The wife let me get a bigger machine to run Ubuntu if we would upgrade her workstation. She's XP and has proprietary software to do her professional work. Of course, it's my fault, the new XP station needs tweaking. Her workstation is German. I CANNOT run a German computer. German code, yes, German Win, no way. The metaphors like "Desktop" and "Windows" end after those two concepts. To tweak then requires selecting menus and radio buttons.

Now, I do own a copy of 64-bit English XP. Can I install the XP on its own partition without it fukn up my working Dapper? And, then, how do I get the GRUB after the XP install? I only want the XP so I can get to the same tweak in English to tweak the German workstation. Things like make the thing fax, network, print to her HP printer ... that sort of thing.

Then after all that, the wife wants a German ubuntu install on her new machine. :D 

Opinions, advice, links to HowTos appreciated.

---

### Post by indytim on 2007-01-31
I did a Windows post-install after having a stable Ubuntu.  Here's the basic's that I did:

1.  Using GParted Live, create a NTFS partition of sufficient size for Windows.
2.  Create a FAT32 partition for any file sharing you want to do between the 2 ops (optional).
3.  Boot to Windows install and install Windows etc in the creted NTFS partition.
4.  If Grub isn't running or has been destroyed by the Windows install, re-install Grub (my favorite is Super Grub --- LiveCD.

There are other approaches, but this worked for me.

Good Luck,

IndyTim

---

### Post by mikewhatever on 2007-01-31
Reinstalling Windows will overwrite the MBR, so that you'll need to restore GRUB. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

---

### Post by Unterseeboot_234 on 2007-01-31
One other thing, and I'll go for it...

I took the largest HD lying around -- 40gig with Win98/ubuntu32 on it to make the C:\ drive for the wife's workstation. Well, to get the HD to format took several attempts back and forth with GParted and Win98 floppy's FDISK. In fact that turned into a unlayering exercise, much like unpeeling an onion. I ended up with a 39gig partition to FAT32 and installed XP.

Now, I seem to think XP should be on NTSF. I read up on Convert.exe at MS "Knowledge Base". They say their program will convert if there is enough room (of course there is on my machine) BUT the MBR on the HD will never be the same is MS thinking.

And, NO, I don't want to reinstall XP on the wife's. I want to leave what I've got going in the way of a setup just the way it is.

The Question: will GRUB fix the MBR? even after a NTSF covert? and does anyone think I should have NTSF format to keep XP "safer"? I know having the linux format on the ubuntu  partition fixed a lot of things when the above-mentioned HD ran both OS.

Thanks, in advance. I've appreciated the answers thus far :)

---

### Post by Sef on 2007-01-31
Read [Restoring GRUB After Installing Windows.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

