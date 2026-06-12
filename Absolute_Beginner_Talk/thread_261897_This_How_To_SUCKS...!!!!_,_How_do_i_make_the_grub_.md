---
title: "This How_To SUCKS...!!!! , How do i make the grub floppy..??"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-09-20
[http://www.linuxjournal.com/article/4622]("http://www.linuxjournal.com/article/4622")

> jason@Hp-Vectra-VL:~$ tar -xzvf /home/jason/Desktop/grub-1.94.tar.gz
grub-1.94/
grub-1.94/AUTHORS
grub-1.94/COPYING
grub-1.94/ChangeLog
grub-1.94/DISTLIST
grub-1.94/INSTALL
grub-1.94/NEWS
grub-1.94/README
grub-1.94/THANKS
grub-1.94/TODO
grub-1.94/Makefile.in
grub-1.94/aclocal.m4
grub-1.94/autogen.sh
grub-1.94/config.guess
grub-1.94/config.h.in
grub-1.94/config.sub
grub-1.94/configure
grub-1.94/configure.ac
grub-1.94/gencmdlist.sh
grub-1.94/gendistlist.sh
grub-1.94/genfslist.sh
grub-1.94/geninitheader.sh
grub-1.94/geninit.sh
grub-1.94/genkernsyms.sh.in
grub-1.94/genmk.rb
grub-1.94/genmoddep.awk
grub-1.94/genmodsrc.sh
grub-1.94/gensymlist.sh.in
grub-1.94/install-sh
grub-1.94/mkinstalldirs
grub-1.94/stamp-h.in
grub-1.94/boot/
grub-1.94/boot/i386/
grub-1.94/boot/i386/pc/
grub-1.94/boot/i386/pc/boot.S
grub-1.94/boot/i386/pc/diskboot.S
grub-1.94/boot/i386/pc/pxeboot.S
grub-1.94/commands/
grub-1.94/commands/boot.c
grub-1.94/commands/blocklist.c
grub-1.94/commands/cat.c
grub-1.94/commands/cmp.c
grub-1.94/commands/configfile.c
grub-1.94/commands/help.c
grub-1.94/commands/ls.c
grub-1.94/commands/search.c
grub-1.94/commands/terminal.c
grub-1.94/commands/test.c
grub-1.94/commands/videotest.c
grub-1.94/commands/i386/
grub-1.94/commands/i386/pc/
grub-1.94/commands/i386/pc/halt.c
grub-1.94/commands/i386/pc/play.c
grub-1.94/commands/i386/pc/reboot.c
grub-1.94/commands/i386/pc/vbeinfo.c
grub-1.94/commands/i386/pc/vbetest.c
grub-1.94/commands/ieee1275/
grub-1.94/commands/ieee1275/halt.c
grub-1.94/commands/ieee1275/reboot.c
grub-1.94/commands/ieee1275/suspend.c
grub-1.94/conf/
grub-1.94/conf/common.mk
grub-1.94/conf/common.rmk
grub-1.94/conf/i386-efi.mk
grub-1.94/conf/i386-efi.rmk
grub-1.94/conf/i386-pc.mk
grub-1.94/conf/i386-pc.rmk
grub-1.94/conf/powerpc-ieee1275.mk
grub-1.94/conf/powerpc-ieee1275.rmk
grub-1.94/conf/sparc64-ieee1275.mk
grub-1.94/conf/sparc64-ieee1275.rmk
grub-1.94/disk/
grub-1.94/disk/loopback.c
grub-1.94/disk/efi/
grub-1.94/disk/efi/efidisk.c
grub-1.94/disk/i386/
grub-1.94/disk/i386/pc/
grub-1.94/disk/i386/pc/biosdisk.c
grub-1.94/disk/ieee1275/
grub-1.94/disk/ieee1275/ofdisk.c
grub-1.94/font/
grub-1.94/font/manager.c
grub-1.94/fs/
grub-1.94/fs/affs.c
grub-1.94/fs/ext2.c
grub-1.94/fs/fat.c
grub-1.94/fs/fshelp.c
grub-1.94/fs/hfs.c
grub-1.94/fs/iso9660.c
grub-1.94/fs/jfs.c
grub-1.94/fs/minix.c
grub-1.94/fs/ufs.c
grub-1.94/fs/sfs.c
grub-1.94/fs/xfs.c
grub-1.94/fs/hfsplus.c
grub-1.94/hello/
grub-1.94/hello/hello.c
grub-1.94/include/
grub-1.94/include/grub/
grub-1.94/include/grub/acorn_filecore.h
grub-1.94/include/grub/arg.h
grub-1.94/include/grub/boot.h
grub-1.94/include/grub/cache.h
grub-1.94/include/grub/device.h
grub-1.94/include/grub/disk.h
grub-1.94/include/grub/dl.h
grub-1.94/include/grub/elf.h
grub-1.94/include/grub/env.h
grub-1.94/include/grub/err.h
grub-1.94/include/grub/file.h
grub-1.94/include/grub/font.h
grub-1.94/include/grub/fs.h
grub-1.94/include/grub/fshelp.h
grub-1.94/include/grub/gzio.h
grub-1.94/include/grub/hfs.h
grub-1.94/include/grub/kernel.h
grub-1.94/include/grub/loader.h
grub-1.94/include/grub/misc.h
grub-1.94/include/grub/mm.h
grub-1.94/include/grub/net.h
grub-1.94/include/grub/normal.h
grub-1.94/include/grub/parser.h
grub-1.94/include/grub/partition.h
grub-1.94/include/grub/pc_partition.h
grub-1.94/include/grub/rescue.h
grub-1.94/include/grub/script.h
grub-1.94/include/grub/setjmp.h
grub-1.94/include/grub/symbol.h
grub-1.94/include/grub/term.h
grub-1.94/include/grub/terminfo.h
grub-1.94/include/grub/tparm.h
grub-1.94/include/grub/types.h
grub-1.94/include/grub/video.h
grub-1.94/include/grub/efi/
grub-1.94/include/grub/efi/api.h
grub-1.94/include/grub/efi/chainloader.h
grub-1.94/include/grub/efi/console.h
grub-1.94/include/grub/efi/console_control.h
grub-1.94/include/grub/efi/disk.h
grub-1.94/include/grub/efi/efi.h
grub-1.94/include/grub/efi/pe32.h
grub-1.94/include/grub/efi/time.h
grub-1.94/include/grub/i386/
grub-1.94/include/grub/i386/linux.h
grub-1.94/include/grub/i386/setjmp.h
grub-1.94/include/grub/i386/types.h
grub-1.94/include/grub/i386/efi/
grub-1.94/include/grub/i386/efi/kernel.h
grub-1.94/include/grub/i386/efi/loader.h
grub-1.94/include/grub/i386/efi/time.h
grub-1.94/include/grub/i386/pc/
grub-1.94/include/grub/i386/pc/biosdisk.h
grub-1.94/include/grub/i386/pc/boot.h
grub-1.94/include/grub/i386/pc/chainloader.h
grub-1.94/include/grub/i386/pc/console.h
grub-1.94/include/grub/i386/pc/init.h
grub-1.94/include/grub/i386/pc/kernel.h
grub-1.94/include/grub/i386/pc/loader.h
grub-1.94/include/grub/i386/pc/memory.h
grub-1.94/include/grub/i386/pc/multiboot.h
grub-1.94/include/grub/i386/pc/serial.h
grub-1.94/include/grub/i386/pc/time.h
grub-1.94/include/grub/i386/pc/vbe.h
grub-1.94/include/grub/i386/pc/vbeblit.h
grub-1.94/include/grub/i386/pc/vbefill.h
grub-1.94/include/grub/i386/pc/vga.h
grub-1.94/include/grub/i386/pc/util/
grub-1.94/include/grub/i386/pc/util/biosdisk.h
grub-1.94/include/grub/ieee1275/
grub-1.94/include/grub/ieee1275/ieee1275.h
grub-1.94/include/grub/ieee1275/ofdisk.h
grub-1.94/include/grub/powerpc/
grub-1.94/include/grub/powerpc/libgcc.h
grub-1.94/include/grub/powerpc/setjmp.h
grub-1.94/include/grub/powerpc/types.h
grub-1.94/include/grub/powerpc/ieee1275/
grub-1.94/include/grub/powerpc/ieee1275/biosdisk.h
grub-1.94/include/grub/powerpc/ieee1275/console.h
grub-1.94/include/grub/powerpc/ieee1275/ieee1275.h
grub-1.94/include/grub/powerpc/ieee1275/kernel.h
grub-1.94/include/grub/powerpc/ieee1275/loader.h
grub-1.94/include/grub/powerpc/ieee1275/multiboot.h
grub-1.94/include/grub/powerpc/ieee1275/time.h
grub-1.94/include/grub/powerpc/ieee1275/util/
grub-1.94/include/grub/powerpc/ieee1275/util/biosdisk.h
grub-1.94/include/grub/sparc64/
grub-1.94/include/grub/sparc64/setjmp.h
grub-1.94/include/grub/sparc64/types.h
grub-1.94/include/grub/sparc64/ieee1275/
grub-1.94/include/grub/sparc64/ieee1275/console.h
grub-1.94/include/grub/sparc64/ieee1275/ieee1275.h
grub-1.94/include/grub/sparc64/ieee1275/kernel.h
grub-1.94/include/grub/sparc64/ieee1275/time.h
grub-1.94/include/grub/util/
grub-1.94/include/grub/util/getroot.h
grub-1.94/include/grub/util/misc.h
grub-1.94/include/grub/util/resolve.h
grub-1.94/io/
grub-1.94/io/gzio.c
grub-1.94/kern/
grub-1.94/kern/device.c
grub-1.94/kern/disk.c
grub-1.94/kern/dl.c
grub-1.94/kern/env.c
grub-1.94/kern/err.c
grub-1.94/kern/file.c
grub-1.94/kern/fs.c
grub-1.94/kern/loader.c
grub-1.94/kern/main.c
grub-1.94/kern/misc.c
grub-1.94/kern/mm.c
grub-1.94/kern/parser.c
grub-1.94/kern/partition.c
grub-1.94/kern/rescue.c
grub-1.94/kern/term.c
grub-1.94/kern/efi/
grub-1.94/kern/efi/init.c
grub-1.94/kern/efi/efi.c
grub-1.94/kern/efi/mm.c
grub-1.94/kern/i386/
grub-1.94/kern/i386/dl.c
grub-1.94/kern/i386/efi/
grub-1.94/kern/i386/efi/init.c
grub-1.94/kern/i386/efi/startup.S
grub-1.94/kern/i386/pc/
grub-1.94/kern/i386/pc/init.c
grub-1.94/kern/i386/pc/lzo1x.S
grub-1.94/kern/i386/pc/startup.S
grub-1.94/kern/ieee1275/
grub-1.94/kern/ieee1275/ieee1275.c
grub-1.94/kern/powerpc/
grub-1.94/kern/powerpc/cache.S
grub-1.94/kern/powerpc/dl.c
grub-1.94/kern/powerpc/ieee1275/
grub-1.94/kern/powerpc/ieee1275/cmain.c
grub-1.94/kern/powerpc/ieee1275/crt0.S
grub-1.94/kern/powerpc/ieee1275/init.c
grub-1.94/kern/powerpc/ieee1275/openfw.c
grub-1.94/kern/sparc64/
grub-1.94/kern/sparc64/cache.S
grub-1.94/kern/sparc64/dl.c
grub-1.94/kern/sparc64/ieee1275/
grub-1.94/kern/sparc64/ieee1275/init.c
grub-1.94/kern/sparc64/ieee1275/openfw.c
grub-1.94/loader/
grub-1.94/loader/efi/
grub-1.94/loader/efi/chainloader.c
grub-1.94/loader/efi/chainloader_normal.c
grub-1.94/loader/i386/
grub-1.94/loader/i386/efi/
grub-1.94/loader/i386/efi/linux.c
grub-1.94/loader/i386/efi/linux_normal.c
grub-1.94/loader/i386/pc/
grub-1.94/loader/i386/pc/chainloader.c
grub-1.94/loader/i386/pc/chainloader_normal.c
grub-1.94/loader/i386/pc/linux.c
grub-1.94/loader/i386/pc/linux_normal.c
grub-1.94/loader/i386/pc/multiboot.c
grub-1.94/loader/i386/pc/multiboot_normal.c
grub-1.94/loader/powerpc/
grub-1.94/loader/powerpc/ieee1275/
grub-1.94/loader/powerpc/ieee1275/linux.c
grub-1.94/loader/powerpc/ieee1275/linux_normal.c
grub-1.94/normal/
grub-1.94/normal/arg.c
grub-1.94/normal/cmdline.c
grub-1.94/normal/command.c
grub-1.94/normal/completion.c
grub-1.94/normal/execute.c
grub-1.94/normal/function.c
grub-1.94/normal/lexer.c
grub-1.94/normal/main.c
grub-1.94/normal/menu.c
grub-1.94/normal/menu_entry.c
grub-1.94/normal/misc.c
grub-1.94/normal/parser.y
grub-1.94/normal/script.c
grub-1.94/normal/i386/
grub-1.94/normal/i386/setjmp.S
grub-1.94/normal/powerpc/
grub-1.94/normal/powerpc/setjmp.S
grub-1.94/partmap/
grub-1.94/partmap/acorn.c
grub-1.94/partmap/amiga.c
grub-1.94/partmap/apple.c
grub-1.94/partmap/gpt.c
grub-1.94/partmap/pc.c
grub-1.94/partmap/sun.c
grub-1.94/term/
grub-1.94/term/terminfo.c
grub-1.94/term/tparm.c
grub-1.94/term/gfxterm.c
grub-1.94/term/efi/
grub-1.94/term/efi/console.c
grub-1.94/term/i386/
grub-1.94/term/i386/pc/
grub-1.94/term/i386/pc/console.c
grub-1.94/term/i386/pc/serial.c
grub-1.94/term/i386/pc/vesafb.c
grub-1.94/term/i386/pc/vga.c
grub-1.94/term/ieee1275/
grub-1.94/term/ieee1275/ofconsole.c
grub-1.94/util/
grub-1.94/util/console.c
grub-1.94/util/grub-emu.c
grub-1.94/util/misc.c
grub-1.94/util/resolve.c
grub-1.94/util/unifont2pff.rb
grub-1.94/util/i386/
grub-1.94/util/i386/efi/
grub-1.94/util/i386/efi/grub-mkimage.c
grub-1.94/util/i386/pc/
grub-1.94/util/i386/pc/biosdisk.c
grub-1.94/util/i386/pc/getroot.c
grub-1.94/util/i386/pc/grub-install.in
grub-1.94/util/i386/pc/grub-mkdevicemap.c
grub-1.94/util/i386/pc/grub-mkimage.c
grub-1.94/util/i386/pc/grub-probefs.c
grub-1.94/util/i386/pc/grub-setup.c
grub-1.94/util/i386/pc/misc.c
grub-1.94/util/powerpc/
grub-1.94/util/powerpc/ieee1275/
grub-1.94/util/powerpc/ieee1275/grub-install.in
grub-1.94/util/powerpc/ieee1275/grub-mkimage.c
grub-1.94/util/powerpc/ieee1275/misc.c
grub-1.94/video/
grub-1.94/video/video.c
grub-1.94/video/i386/
grub-1.94/video/i386/pc/
grub-1.94/video/i386/pc/vbe.c
grub-1.94/video/i386/pc/vbeblit.c
grub-1.94/video/i386/pc/vbefill.c

jason@Hp-Vectra-VL:~$ cd grub_1.94
bash: cd: grub_1.94: No such file or directory
jason@Hp-Vectra-VL:~$ ./configure
bash: ./configure: No such file or directory
jason@Hp-Vectra-VL:~$ make
make: *** No targets specified and no makefile found.  Stop.
jason@Hp-Vectra-VL:~$ make instal
make: *** No rule to make target `instal'.  Stop.
jason@Hp-Vectra-VL:~$



Well...?! , It sure dosen't work....[-X 

Any idea's..??

---

### Post by luv2craftca on 2006-09-20
you made a mistake when you typed the directory name.  You used an underscore '_' instead of a dash '-' in 

jason@Hp-Vectra-VL:~$ cd grub_1.94
bash: cd: grub_1.94: No such file or directory

see the line below which is from your post
grub-1.94/video/i386/pc/vbefill.c

---

### Post by etc on 2006-09-20
> 
jason@Hp-Vectra-VL:~$ cd grub_1.94

That's your problem right here, grub_1.94 isn't grub-1.94

So try
```

cd grub-1.94
./configure
make && sudo make install

```

You should also have the build-essential metapackage installed, and the other packages needed to compile grub installed too, so do
```
sudo apt-get install build-essential
sudo apt-get build-dep grub
```
before the first step if you run into problems

---

### Post by jason.b.c on 2006-09-20
Why dosen't this one work then..?

> mkdir -p /floppy/boot/grub
cp /usr/local/share/grub/i386-pc/stage*/floppy/boot/grub

Thats all i really need isn't it..??  I already have grub installed on my hard drive..

---

### Post by confused57 on 2006-09-20
I'm not sure what you're wanting to do, but if you're trying to install your current installation grub to floppy:

[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

---

### Post by jason.b.c on 2006-09-20
> **confused57 said:**
> I'm not sure what you're wanting to do, but if you're trying to install your current installation grub to floppy:

[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

YEA , I'm trying to make a grub boot floppy..

Just in case i ever need it...;)

---

### Post by jason.b.c on 2006-09-20
So does this mean it's made now..?

```
jason@Hp-Vectra-VL:~$ sudo mount /media/floppy0
Password:
jason@Hp-Vectra-VL:~$ sudo mkdir -p /media/floppy0/boot
jason@Hp-Vectra-VL:~$ sudo cp -r /boot/grub /media/floppy0/boot
jason@Hp-Vectra-VL:~$ sudo umount /media/floppy0
jason@Hp-Vectra-VL:~$


```

:confused:

---

### Post by confused57 on 2006-09-20
Guess you could try booting your computer with the grub floppy to see if it works.

---

### Post by jason.b.c on 2006-09-24
Well i finally got around to trying out this grub disk i made , Because of recent storm activity in my area i was forced to shutdown my computer...

So when i was able to start up again i thought i would give this thing a shot , And gues what..?  

IT DOSEN"T EVEN WORK..!

> **This is not a bootable disk , Please insert one that is and press enter when ready.**

So where did i go wrong..? , Has anyone here actually been successfully able to make one..??

Could you tell me how you did it...???

---

### Post by .t. on 2006-09-24
You need to install the grub boot sector on your floppy.
Do this:```
sudo -s
grub-install /dev/fd0
mount /media/floppy0
cp -r /boot/grub /media/floppy0
umount /media/floppy0
```
Reboot, and tell me if that works.

---

### Post by jr.gotti on 2006-09-24
Call me tired and grumpy, because I am, I guess.

But could you **please **stop complaining about everything? I realize you're new to the whole linux thing and it _can_ be intimidating, but honestly man!

> And gues what..?  IT DOSEN"T EVEN WORK..!Welll, guess what buddy! You did something wrong, and we'd be more than happy to help you figure out what it is if you would stop "shouting." (Yes...typing in all caps is considered "shouting" on internet forums, and bothers a lot of people.) Read up on forum etiquitte. Use it.

I don't have experience installing grub to a floppy, mainly because I don't have a floppy drive, but just from your first post I can see you have issues with the command line. As others have pointed out, make sure you're changing into the correct directory. If it says "Directory not found" Or something to that effect, guess what?! The directory doesn't exist. Try again, and check your spelling.

Also, I don't think this was pointed out, but in your "make install" step (not that it mattered, you weren't in the source dir) you spelled "install" as "instal." That tends to be counter-productive in the whole "working" thing.

Again...I'm nit-picking, but people will be more likely to want to help if your not using all caps, throwing haphazardly selected exclamation points, question marks, underscores, and periods into your post, and if you make sure your not making blatantly obvious mistakes, such as typographical errors.

And one last thing, to say that "This How_TO SUCKS!!!!!, ...." is EXTREMELY insulting and rude to whoever may have written it. Just because you don't understand it doesn't mean it "SUCKS." They took their  time to write that for the benefit of the community and your lack of appreciation is appalling.

OkAy...!!? I'm dUn_! GOING TO SLEP FOR THE Fir_St TImE i!! ,n....,36..! hOU"rS.

Puheace!
-Gotti

---

### Post by jason.b.c on 2006-09-24
> **pixelPOET said:**
> Call me tired and grumpy, because I am, I guess.

But could you **please **stop complaining about everything? I realize you're new to the whole linux thing and it _can_ be intimidating, but honestly man!

Welll, guess what buddy! You did something wrong, and we'd be more than happy to help you figure out what it is if you would stop "shouting." (Yes...typing in all caps is considered "shouting" on internet forums, and bothers a lot of people.) Read up on forum etiquitte. Use it.

I don't have experience installing grub to a floppy, mainly because I don't have a floppy drive, but just from your first post I can see you have issues with the command line. As others have pointed out, make sure you're changing into the correct directory. If it says "Directory not found" Or something to that effect, guess what?! The directory doesn't exist. Try again, and check your spelling.

Also, I don't think this was pointed out, but in your "make install" step (not that it mattered, you weren't in the source dir) you spelled "install" as "instal." That tends to be counter-productive in the whole "working" thing.

Again...I'm nit-picking, but people will be more likely to want to help if your not using all caps, throwing haphazardly selected exclamation points, question marks, underscores, and periods into your post, and if you make sure your not making blatantly obvious mistakes, such as typographical errors.

And one last thing, to say that "This How_TO SUCKS!!!!!, ...." is EXTREMELY insulting and rude to whoever may have written it. Just because you don't understand it doesn't mean it "SUCKS." They took their  time to write that for the benefit of the community and your lack of appreciation is appalling.

OkAy...!!? I'm dUn_! GOING TO SLEP FOR THE Fir_St TImE i!! ,n....,36..! hOU"rS.

Puheace!
-Gotti


Boy. , You were really helpfull..[-X 

For one thing , I put part of the title of this thread in capitals to draw attention to it..

secondly - i don't have "issues" with the command line..!! , I merely have trouble trying to remember every little thing that i'm supposed to type in it , Like trying to remember if i'm supposed to use a ** dpkg -i** or a **tar -xvfw** or any of the other letters that are used in the terminal to do certain things...How am i supposed to remember everything..?

But i guess you do though , Must be those "super human" qualities you picked up.

Third - the first post i made wasn't correct to begin with , I relized i was doing it wrong when i found out i didn't need to download grub..

I thought that grub thing i downloaded from that page was to make the grub disk with but i was incorrect and soon found out there was a how-to here in the forum wich i tried and it didn't seem to work the way it was suppose to..

So yes..! I did something wrong.!

Fourth - I used the capitals in my last post to express aggrevation not to be insulting ( you should try to learn the differances between the two ) I appologize if anyone was insulted...

> and if you make sure your not making blatantly obvious mistakes, such as typographical errors. 
I don't alway's know when i'm making obvious mistakes.

---

### Post by jason.b.c on 2006-09-24
> **.t. said:**
> You need to install the grub boot sector on your floppy.
Do this:```
sudo -s
grub-install /dev/fd0
mount /media/floppy0
cp -r /boot/grub /media/floppy0
umount /media/floppy0
```
Reboot, and tell me if that works.

Ah crud.! , Nows there's nothing on the disk.:( 

I can't figure out that happened..It had all the other stuff on it before..:confused:

---

### Post by .t. on 2006-09-24
Hmm. Sorry; I was just reading the man pages. It shouldn't do that - it didn't to my HD. However; does it load GRUB, or has it messed up the format? It sounds likely that that's what it's done.

---

### Post by jason.b.c on 2006-09-24
> **.t. said:**
> Hmm. Sorry; I was just reading the man pages. It shouldn't do that - it didn't to my HD. However; does it load GRUB, or has it messed up the format? It sounds likely that that's what it's done.

Uh oh , What do you mean by HD..???  Hard drive.? I hope it didn't mess up my hard drive's grub..

Nah , now there's just nothing on the floppy at all...

---

### Post by .t. on 2006-09-24
grub-install is the program used to install grub. It is run during the installation so that you can boot off your HD - hard drive. It shouldn't be dangerous, if you know what you're doing.

And could you elaborate on "Nah". "Nah" to what? It doesn't boot? The format's messed up? Can you mount it? If so, why didn't it copy /boot/grub when you did the instructions I gave you?

---

### Post by xpod on 2006-09-24
> I merely have trouble trying to remember every little thing that i'm supposed to type in it 

Sorry to hear your woes but cant you just "copy & paste" commands from a "how to" as it makes for less typo`s.....I KNOW!!!:D 

Try not get so upset over a daft floppy mate.Even though your floppy aint booting im sure your pc IS which is more than some poor peoples are.

Try taking a "step back"...thats what i find is the best bet when im too wrapped up in some confusing enigma.....It`s usually just ME who is confused

I know those "how to`s" can be hard at times but it`s usually not their fault if it goes wrong as much as it is our own

EDIT..Good luck regardless....deep breaths m8:D

---

### Post by jason.b.c on 2006-09-24
> **.t. said:**
> grub-install is the program used to install grub. It is run during the installation so that you can boot off your HD - hard drive. It shouldn't be dangerous, if you know what you're doing.

I understand that part , I have grub installed already to my hard drive and ubuntu boots just fine.

> And could you elaborate on "Nah". "Nah" to what? It doesn't boot? The format's messed up? Can you mount it? If so, why didn't it copy /boot/grub when you did the instructions I gave you?

I meant that there is now nothing at all on the floppy disk because there was something on it before..

It dosen't boot , nor did it before with the previous instructions from other's ( not your's )..

I can mount the floppy but that's it because well it's empty..

---

### Post by steve.horsley on 2006-09-24
IIRC, you make a GRUB boot floppy by copying stage1 and stage2 to it. You do **not** mount the floppy first because you write raw to it. Ididn't do it the way the readme said. I made a floppy image file first like this:
**cat stage1 stage2 > grub-floppy.img**
Then I wrote this to the floppy like this:
**dd if=grub-floppy.img of=/dev/fd0**

Result:  a bootable grub floppy disk. You can't mount it, it hasn't got a filesystem. But it's bootable and gives a GRUB prompt.

---

### Post by jason.b.c on 2006-09-24
> **steve.horsley said:**
> IIRC, you make a GRUB boot floppy by copying stage1 and stage2 to it. You do **not** mount the floppy first because you write raw to it. Ididn't do it the way the readme said. I made a floppy image file first like this:
**cat stage1 stage2 > grub-floppy.img**
Then I wrote this to the floppy like this:
**dd if=grub-floppy.img of=/dev/fd0**

Result:  a bootable grub floppy disk. You can't mount it, it hasn't got a filesystem. But it's bootable and gives a GRUB prompt.

Are you sure about this..?

> jason@Hp-Vectra-VL:~$ cat stage1 stage2 > grub-floppy.img
cat: stage1: No such file or directory
cat: stage2: No such file or directory
jason@Hp-Vectra-VL:~$



I guess this shouldn't happen..

---

### Post by crokett on 2006-09-24
> **jason.b.c said:**
> Are you sure about this..?
```
jason@Hp-Vectra-VL:~$ cat stage1 stage2 > grub-floppy.img
cat: stage1: No such file or directory
cat: stage2: No such file or directory
jason@Hp-Vectra-VL:~$
```


I guess this shouldn't happen..

What directory are you in?  My system has the files stage1 and stage2 in /boot/grub

so it would be thusly:
```
cd /boot/grub
sudo cat stage1 stage2 > grub-floppy.img

```
      or you could skip the cd command and do
```

      sudo cat /boot/grub/stage1 /boot/grub/stage2 > grub-floppy.img

```
Either of what I just told you worked for me 

Just make sure you are putting the .img file in a directory you have write acces to - such as your home directory



Not trying to be snippy but I'd suggest googling navigating linux and what a fully qualified pathname is.  That is basic computer use stuff

---

### Post by jason.b.c on 2006-09-25
:-k :confused:

---

### Post by jason.b.c on 2006-09-25
> **crokett said:**
> What directory are you in?  My system has the files stage1 and stage2 in /boot/grub

so it would be thusly:
```
cd /boot/grub
sudo cat stage1 stage2 > grub-floppy.img

```
      or you could skip the cd command and do
```

      sudo cat /boot/grub/stage1 /boot/grub/stage2 > grub-floppy.img

```
Either of what I just told you worked for me 

Just make sure you are putting the .img file in a directory you have write acces to - such as your home directory



Not trying to be snippy but I'd suggest googling navigating linux and what a fully qualified pathname is.  That is basic computer use stuff

HUH.?

> jason@Hp-Vectra-VL:~$ cd /boot/grub
jason@Hp-Vectra-VL:/boot/grub$ sudo cat stage1 stage2 > grub-floppy.img
bash: grub-floppy.img: Permission denied
jason@Hp-Vectra-VL:/boot/grub$ sudo cat /boot/grub/stage1 /boot/grub/stage2 > grub-floppy.img
bash: grub-floppy.img: Permission denied
jason@Hp-Vectra-VL:/boot/grub$
:confused:

---

### Post by crokett on 2006-09-25
> **jason.b.c said:**
> HUH.?
jason@Hp-Vectra-VL:~$ cd /boot/grub
jason@Hp-Vectra-VL:/boot/grub$ sudo cat stage1 stage2 > grub-floppy.img
bash: grub-floppy.img: Permission denied
jason@Hp-Vectra-VL:/boot/grub$ sudo cat /boot/grub/stage1 /boot/grub/stage2 > grub-floppy.img
bash: grub-floppy.img: Permission denied
jason@Hp-Vectra-VL:/boot/grub$
:confused:

[QUOTE=crokett]
[B]Just make sure you are putting the .img file in a directory you have write acces to - such as your home directory
[/[B]
[/QUOTE]

Again.... basic computer use stuff.  Linux is telling you you don't have access to write to /boot/grub  so you need to put the file someplace else:

```

sudo cat /boot/grub/stage1 /boot/grub/stage2 > /home/<jason'shomedir>/grub-floppy.img
```

After this, run the dd command that was given to you in an earlier post 

NOTE: <jason'shomedir> should be replaced with your actual home directory name.  There isn't an actual directory on your system called <jason'shomedir>.  If you don't know how to get to your home dir, see my previous post on reading up on navigating linux - again basic stuff.  Same principles apply going all the way back to DOS.

---

### Post by jason.b.c on 2006-09-25
So does this mean it's written now..?  

> jason@Hp-Vectra-VL:~$ sudo cat /boot/grub/stage1 /boot/grub/stage2 > /home/jason/grub-floppy.img
Password:
jason@Hp-Vectra-VL:~$ dd if=/home/jason/grub-floppy.img of=/dev/fd0
dd: writing to `/dev/fd0': Input/output error
17+0 records in
16+0 records out
8192 bytes transferred in 1.178276 seconds (6953 bytes/sec)
jason@Hp-Vectra-VL:~$


What's that input/output error..?

---

### Post by dmizer on 2006-09-25
nope, not written yet.

try this instead:

```
fdformat /dev/fd0
dd if=/home/jason/grub-floppy.img of=/dev/fd0 bs=1440k
```

---

### Post by .t. on 2006-09-25
Yeah. But he'll need to use```
sudo fdformat /dev/fd0
sudo dd if=/home/jason/grub-floppy.img of=/dev/fd0 bs=1440k
```

His normal user doesn't have raw write access to /dev/fd0

---

### Post by jason.b.c on 2006-09-26
> **.t. said:**
> Yeah. But he'll need to use```
sudo fdformat /dev/fd0
sudo dd if=/home/jason/grub-floppy.img of=/dev/fd0 bs=1440k
```

His normal user doesn't have raw write access to /dev/fd0

This look OK now..?

> jason@Hp-Vectra-VL:~$ sudo fdformat /dev/fd0
Password:
Double-sided, 80 tracks, 18 sec/track. Total capacity 1440 kB.
Formatting ... done
Verifying ... Problem reading cylinder 0, expected 18432, read 8192
jason@Hp-Vectra-VL:~$ sudo dd if=/home/jason/Desktop/grub-floppy.img of=/dev/fd0 bs=1440k
0+1 records in
0+1 records out
106088 bytes transferred in 5.700752 seconds (18609 bytes/sec)
jason@Hp-Vectra-VL:~$

:D 

Except for cyl 0..    But it formatted anyway..

---

### Post by dmizer on 2006-09-26
> **jason.b.c said:**
> ```
Verifying ... Problem reading cylinder 0, expected 18432, read 8192
```

that could very well have been most of your problem to begin with.  that floppy's probably bad.

---

### Post by .t. on 2006-09-26
It might still work. Does it?

---

### Post by adrian15 on 2006-09-27
> **jason.b.c said:**
> [http://www.linuxjournal.com/article/4622]("http://www.linuxjournal.com/article/4622")



Well...?! , It sure dosen't work....[-X 

Any idea's..??


You're trying to make a grub2 floppy. Grub legacy is the one that Ubuntu uses... which it is 0.97 version.

The easiest way for making a grub floppy is downloading one already made which has a lot of options called. Super Grub Disk.

[Super Grub Disk Floppy inside a bz2 file.]("http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=97")

Download the file.
bunzip2 file.bz2
Insert a blank disk on your floppy disk
dd if=./file of=/dev/fd0
Reboot with the floppy you're done.

You can also download a [grub cdrom]("http://adrian15.raulete.net/grub/") from Super Grub Disk site and burn it with k3b or whatever burning program.

adrian15

---

