---
title: "Quik"
date: 2005-04-21
forum: Apple PPC Users
---

### Post by piltdownman on 2005-04-21
I have a beige g3 with ubuntu 5.04 installed on it. It boots fine into linux using bootx, but out of curiosity I'd like to see if quik could work. So far I have been able to get quik to load in open firmware, and it sees the drive it needs to boot from. However, when it tries to load the kernel it spits out an error something like this:

Read error on block (block number that the kernel is located at)
Read error on block (same, this changes if I specify a different kernel)
Image not found.... try again

I've been looking around the web and reading various message boards. It seems like there is NO documentation for quik, just a smattering of posts about it.

Any help would be appreciated, but this is by no means a critical problem (I'm just messing about)

---

### Post by piltdownman on 2005-04-23
To answer my own question, all that I needed to do was change the load base in open firmware:

setenv load-base F00000

Now I'm booting directly from open firmware  :grin: !

---

### Post by farruinn on 2005-04-27
This is good news!  To my knowledge quik does not work well on these models.  I have a beige G3 and I've always had to use bootx.  You may want to share your experiences with the developer, simonrvn on the #debianppc channel.

---

### Post by Suparious on 2005-04-28
This would be fantastic!

BTW, did dyou need to use Xpostfacto to boot the install CD? I have a Beige G3 300MHz, which I have 10.3.x running on it and even if I disable aqua it still takes 1-2secs to resolve a hostname. I would like to use it as my primary nameserver and pop/smtp/webmail server. I don't care is mail is slow, but 2secs to translate a name to an IP is just to long.

I figured that I would try opendarwin, but I really have no attachments to the Mac. I simply bought my G3 (for $100CDN!!) to learn how to troubleshoot mac's for my work (I'm a TSR for an ISP). I began investigating other distros for my mac and was quite happy to understand that PPC support was in the kernel.

I have been successfully running Ubuntu 5 on my two Athlon machines. One with MythTV as my PVR/game station, the other is my personal desktop. Ubuntu has been flawless (despite OpenGL [which I finally got working on my R300], but that's ATI's poor dirver support). Unless I can find something somewhere, I would like to make a step-by-step checklist to getting ubuntu on my beige g3.

Shaun

---

### Post by farruinn on 2005-04-28
Even if you are unable to get the quik bootloader to work for you, you can always use bootx (from a minimal OS 9 partition) as the bootloader:
[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)
[http://www.ubuntulinux.org/wiki/bootx](http://www.ubuntulinux.org/wiki/bootx)

---

### Post by piltdownman on 2005-04-29
I have an OS 9 install on a separate disk that I use to launch bootx.  It would have taken months of work to get ubuntu installed and quik working without bootx.  I'm not saying it isn't do-able, it just wasn't something I was willing to try.  However, because my OS 9 install was on a separate disk I can simply remove it and have a MacOS free system. (Conversely when I screw something up, I will be able to re-attach the disk an return to the safety of bootx.)

---

### Post by piltdownman on 2005-05-15
In case anyone is interested, these are my open firmware settings and my quik.conf:

**Open Firmware** 

little-endian?  false
real-mode?      false
auto-boot?      false
diag-switch?    false
fcode-debug?    false
oem-banner?     false
oem-logo?       false
use-nvramrc?    true
real-base       0xffffffff
real-size       0x100000
virt-base       0xffffffff
virt-size       0x100000
load-base       0x600000
pci-probe-list  0xffffffff
screen-#columns 0x64
screen-#rows    0x28
selftest-#megs  0x0
boot-device     /pci/Apple53C875Card/sd@0:0
boot-file       /pci/Apple53C875Card/sd@0:2/vmlinux root=/dev/sda2
diag-device     
diag-file       
input-device    kbd
output-device   screen
oem-banner      
oem-logo        
nvramrc         hex
                : $D find-device ;
                : $E device-end ;
                : $L BLpatch ; : $R BRpatch ;
                : $X execute ;
                : $p 0 to my-self property ;
                : $a " /chosen" $D $p $E ;
                : helpb ['] install-interrupt-vectors ['] noop $R
                0 4000 release-mem 8000 2000 release-mem ;
                10 buffer: km
                dev kbd
                get-key-map km swap move
                $E
                : ck 0 do swap dup 3 >> km + c@ 1 rot 7 and << and or loop ;
                : bootr 0d word count encode-string " machargs" $a
                0 0 1 ck if 0 and else f 3d 0 2 ck if 40 or then then
                if bye else helpb 1e 0 do ['] boot catch drop 1f4 ms loop then bye ;
                : myboot boot-command eval ;
                dev /packages/mac-parts
                : $M 7F00 - 4 ;
                ' my-init-program 34 + ' $M $L
                ' load-partition dup
                80 + ' 2drop $L
                104 + ' 0 $L
                ' load 15C + ' 0 $L
                $E
                dev /packages/obp-tftp
                : $M dup 24 - HIS-ENET-HA 6 move 14 + ;
                ' open 66C - ' $M $L
                $E
                dev mac-io
                : decode-unit parse-1hex ;
                $E
                unselect-dev
boot-command    0 bootr

(notice the boot-file setting, i think there just has to be *something* there, for more info go [here](http://lists.debian.org/debian-powerpc/2001/03/msg00361.html) 
)

**/etc/quik.conf** 

default=Linux
timeout=100
partition=2

image=/vmlinux
        root=/dev/sda2
        label=Linux
        read-only



I'm using quik version 2.1-6 which I had to get from debian unstable.  To get a kernel to actually load from quik, I had to compile a kernel with scsi support included not as a module.  At this point everything seems to be working nicely except that the bottom 3rd of my screen in X is covered in verticle lines and is near unreadable -I'm not sure what to do about this.

---

