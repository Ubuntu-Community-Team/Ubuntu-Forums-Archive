---
title: "Triple Booting help"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by cumanzor on 2007-03-31
Hello all, long time no see.

I currently have XP Pro and Vista installed in my first disk, each in its own partition. I'm giving Vista a test drive before moving to it. I read about the seamless virtualization with Qemu and Ubuntu 7.04, and found it to be intersting so I want to try it out.

I downloaded and burned a copy of the 7.04 beta release, and I'm planning to install it into my second hard drive. I've never been able to boot Ubuntu from this drive. I end up with Grub error 17 or whatever.

Problem WAS this. Grub was installed in the MBR of my first drive, overwriting the NTLDR, while ubuntu was installed in my second drive. I ended up with some error, unable to boot either XP or Ubunutu. The only way I managed to install it was in my first disk, in a partition next to XP. But I don't have any more space in my first disk and I don't feel like erasing the vista partition since I'm still testing some programs to see if they'll work.

Now, this adds another problem. Can grub boot into winload.exe? Vista uses winload.exe to boot either XP's legacy boot loader (NTLDR) or Windows Vista, and apparently, it is very sensitve to HD changes.

Basically, what I want is this:

XP and Vista in a Disk 1
Ubuntu in Disk 2.

---

### Post by STREETURCHINE on 2007-03-31
i have mine set so that at start i tap f11 and it brings up the option which hard drive to boot from,

to do it i unplugged the first hard drive and then just installed windows on the second drive

when it was finished i just had to plug in the first harddrive  reboot.hit f11  continually till it starts

that is how i solved it but you may want another way

---

### Post by celticbhoy on 2007-03-31
On the same thought I have a new pc with Vista on the main drive and I have put the drive from my old PC in which contains Ubuntu & XP when I set the old drive as the first boot device grub loads ok with the menu entries, but when I try to boot ubuntu it freezes on load screen, and XP just reboots the PC. Is this becuase the new drive is Sata and the old is IDE, would that complicate the problem

---

