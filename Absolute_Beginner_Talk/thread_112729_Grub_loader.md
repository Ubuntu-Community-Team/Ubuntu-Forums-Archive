---
title: "Grub loader"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by R3linquish3r on 2006-01-04
Here is my lst file. My problem is when i try to boot windows it says NDTFS (or something near that) missing. Press CTRL+ALT+DEL to restart. How can I fix this?

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/mapper/Ubuntu-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,0)
kernel		/vmlinuz root=/dev/mapper/Ubuntu-root ro quiet splash
initrd		/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root		(hd0,0)
kernel		/vmlinuz root=/dev/mapper/Ubuntu-root ro single
initrd		/initrd.img
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-amd64-generic root=/dev/mapper/Ubuntu-root ro quiet splash
initrd		/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-amd64-generic root=/dev/mapper/Ubuntu-root ro single
initrd		/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin  
boot

title		Windows XP Pro
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by benplaut on 2006-01-04
A few questions:

Did you install Ubuntu after windows?

Did you thoroughly defragment your drive before installing?

--

The basic process involves putting in the windows install CD, going into 'recover mode', then typing in the command: "fixmbr"... i've never doen it, though - wait for someone who has to answer and back me up :P

Good luck!

---

### Post by R3linquish3r on 2006-01-04
yes i installed ubuntu after windows. windows is on a SATA drvie, ubunutu is on an IDE drive. If ubuntu defraged the harddrive before it was isntalled then yes.

---

### Post by R3linquish3r on 2006-01-05
ummmm anyone got any ideas?

---

### Post by R3linquish3r on 2006-01-05
Ok I found out it's saying NTLDR is missing. Anyone have a clue waht this means?

---

### Post by jonathanm on 2006-01-05
if u gt into your ubuntu install then you can check if there really is an ntldr file missing, go into your /media/hda? or wherever it is and have a look.

My Grandad had this problem and we had to reinstall windows but i'll send you a pm with my ntldr file if you want to try and copy it over

---

### Post by R3linquish3r on 2006-01-05
alright that'll work. ill cehck now. if i put in ure ntldr file will grub still boot it? isnt ntldr window's booter?

---

### Post by jonathanm on 2006-01-05
i havent found a way of sending you my ntldr file yet pm wont allow attachments
i dont know if itll work but it cant do any worse as long as you back up your original ntldr

---

### Post by R3linquish3r on 2006-01-05
yeah i found it it's sitting there. should i put in my linux cd and re-install grub? or do you tihnk its a problem with my menu.lst?

---

### Post by jonathanm on 2006-01-05
i think its probably a problem with windows rather than linux or grub
can you give me your email and ill send it to you

---

### Post by R3linquish3r on 2006-01-05
wait another solution i came up with....

my windows drive is a SATA. should i ahve it say shd1 isntead of hd1?

---

### Post by R3linquish3r on 2006-01-05
my email is [email]godeaglewcw@hotmail.com[/email]

---

### Post by jonathanm on 2006-01-05
ok thats sent, but i think that grub is working as it is, ive seen windows give this error message which means that grub has succeeded in trying to boot windows but that the windows bootloader (ntldr) is not working.

---

### Post by R3linquish3r on 2006-01-05
gatcha ill try putting yours in. ill email ya if it works 

thx :D

---

### Post by jonathanm on 2006-01-05
kl

---

### Post by R3linquish3r on 2006-01-05
havent gotten the email yet :(

---

