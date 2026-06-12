---
title: "Slitaz won't boot"
date: 2012-02-07
forum: Any Other OS
---

### Post by Old Pink on 2012-02-07
Brand new fresh installation. Laptop boots, GRUB loads fine, one option:
> 
"SliTaz GNU/Linux (cooking) (Kernel vmlinuz-2.6.30.6-slitaz)"

Choose this. Laptop displays:
> 
Booting 'SliTaz GNU/Linux (cooking) (Kernel vmlinuz-2.6.30.6-slitaz)'

root hd(0,0)
Filesystem time is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.30.6-slitaz root=/dev/hda1
[Linux-bzImage, setup=0x3000, size=0x21a850]

And hangs.

Sounds very similar to this problem: [http://www.linuxquestions.org/questions/linux-kernel-70/machine-hangs-on-boot-kernel-or-initrd-not-loaded-747650/](http://www.linuxquestions.org/questions/linux-kernel-70/machine-hangs-on-boot-kernel-or-initrd-not-loaded-747650/) but I can't find a suitable initrd.img installed, and there are no BIOS options I can change that make any effect.

Quick fix, please? I think it's just something to do with GRUB being set up wrong, but I might be wrong...?

---

### Post by Old Pink on 2012-02-07
I've tried changing root=/dev/hda1 to hda, hda0, sda, sdb, sda1, sda2, sdb1, and pretty much anything else you can imagine. 

That seems to solve this problem a lot of the time, but I simply can't figure it out.

---

### Post by oldfred on 2012-02-07
Post this so we can see your entire configuration.

wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'xz
chmod a+x bootinfoscript
sudo bash bootinfoscript

Above is test versions which has some fixes. If you need instructions, this is standard version, you also may need gawk and xz:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

