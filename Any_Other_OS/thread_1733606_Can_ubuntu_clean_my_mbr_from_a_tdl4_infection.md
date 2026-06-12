---
title: "Can ubuntu clean my mbr from a tdl4 infection?"
date: 2011-04-19
forum: Any Other OS
---

### Post by victux1 on 2011-04-19
I've been using ubuntu for several years. The 10.10 AMD64 version is going great for me, and I do everything with it, so that, today, I can proudly say I do not need Windows at all (or almost...)

My netbook is partitioned so that offers to start the grub bootloader or the windows bootloader, which in turn allows me to choose between loading Windows Vista or Windows 7. The reason I have not yet rid off the "dark side" is simple:  Windows Vista OS came with the netbook, and I have found that, using my notebook with the battery, results to be the OS which allows for lower power and greater autonomy.

Using Windows 7, I've got a bellicose virus, and I fought with him awhile, but soon I realized that I got the MBR infected :-( (and nothing less than by a monstrous freak: @ TDL4 the MBR rootkit). I fought (various AV and ASpyware tools) from both the Vista and the Seven systems. The last thing I can remember is me identifying the problem in the MBR by using the aswMBR.exe program, which offered to fix it easily, and the computer restarted. A bad move, perhaps? ... Now, when I choose to enter the Windows boot I can select them, bat neither windows vista nor windows 7 are successfull. Both of them start loading but they soon give me a pretty blue screen of death, and then the computer restarts. Of course, I 've got no success even trying safe mode or the last known good configuration option, or anything. It's now quite impossible to start any of my two modern windows systems.

In spite of the days of study, I suspect that it might be an impossible task ... I can only use Ubuntu now. Well, no problem, since from ubuntu I do access my data on the other partitions perfectly, and this OS is running smoothly... 

The question is: Can you think of any wayUbuntu to correct, or to clean, the MBR from that damn monster virus, and I can boot my windows systems again? (It seems that there may be not free solutions (eg warrior cd), but Linux should get a way to this, and I'm even sure, given the power that Linux has, although perhaps no one has bothered to develop anything close to these not free solutions)

Running Kaspersky's TDSSKiller throught Wine I get a "can't load driver" error, but, anyway, I think it&#347; not the correct approach. Any idea, like methods to scan, to browse or manipulate the mbr will be wellcome.):P

---

### Post by mips on 2011-04-19
Are you sure it's the MBR that is cooked? If the MBR is cooked how do you boot ubuntu?

From a terminal in ubuntu type **sudo fdisk -l** and post the output here.

**[COLOR="Red"]WARNING[/COLOR], use this information with extreme caution!**
You can repair the MBR from the Windows install media using the **fixmbr** command.

In linux you can erase the mbr using dd
# dd if=/dev/null of=/dev/sdX bs=446 count=1

# dd if=/dev/null of=/dev/sdX bs=512 count=1 will not only erase the mbr but also the **partition table** [COLOR="red"]**You have been warned!**[/COLOR]

---

### Post by victux1 on 2011-04-19
[SIZE=2]Thanks a lot, you make me feel **I'm not alone in the Universe** :D

The awsMBR.exe program, from Avast!, showed me this:
[http://img171.imageshack.us/i/aswmbrpantallazo.png/](http://img171.imageshack.us/i/aswmbrpantallazo.png/)
So I clicked *fix*, then I think it [/SIZE][SIZE=2]did a reboot, and from that moment, I always got BSOD ( as I told).

Certainly, **I already tried that you say **(exactly,[/SIZE][SIZE=2] I did:* [COLOR=Blue]dd if=/dev/zero of=/dev/sda bs=512 count=1[/COLOR]* ), but just after I got my partition table backup, with [/SIZE][SIZE=2]*[COLOR=Blue][COLOR=#3366ff]sfdisk -d /dev/sda > table[/COLOR][/COLOR]*. Of course I restored it when my mbr was filled with zeros. I restored it with:[/SIZE][SIZE=2][COLOR=#3366ff] sfdisk --force /dev/sda <[/COLOR][COLOR=#3366ff] table. [COLOR=Black]And I reinstalled and updated the grub-pc too, of course.[/COLOR]

[/COLOR][/SIZE][SIZE=2]But..., when I rebooted the netbook, and I choosed the windows loader option, at the grub menu, both windows systems didn't start yet. And, what is worse, both went to a black screen and rebooted the system very quickly. Using the windows seven safe mode, I could read something like this *"error selecting the booting, it&#347; not posible to access to a required device"* (it's just a translation of the real warning, since I am a spaniard). Before filling the mbr with zeros, I got BSOD screens, but I could see my windows vista desktop a few seconds, before system had gone to BSOD. So, as I had done a full mbr backup too, I have had to restore it, trying to revert to the original situation.

 I think that filling mbr with zeros and then restoring just the partition table [/SIZE][SIZE=2]** is not the solution, unless I could know what to do in order to boot in my windos systems again**. Perhaps it's a correct solution if one just wants to reinstall windows with a clean mbr (with no bootkit or whatever), as far as I know. But I would prefer to start my windos systems already installed, because if it's not possible, TDL4 would have won this game, and no approach would be successful from my solid ubuntu partition.

(I Hope my english be understandable.)[/SIZE]

P.S.: fdisk -l
Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x87b8bc45
Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        1698    13631488   27  Desconocido ----> just the acer's pqservice partition
/dev/sda2   *        1698       28217   213015548    7  HPFS/NTFS     ----> This is W Vista, and it has the W 7 bootloader
/dev/sda3           28217       37384    73632764    7  HPFS/NTFS      ----> This is W 7
/dev/sda4           37385       38913    12281662    5  Extendida
/dev/sda5           37385       38842    11711353+  83  Linux
/dev/sda6           38843       38913      570276   82  Linux swap / Solaris[SIZE=2][COLOR=#3366ff]
[/COLOR]  [/SIZE]

---

### Post by victux1 on 2011-04-20
Yeah! Finally, I could boot my windows sytems, using w vista and w 7 repair disks (I got them at [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/))

Firts of all, as a good and rational caution, I had used the command dd, to erase my mbr, and then I have restored my partition table, previously saved, by using sfidk.

Then I have used the w 7 repair disk, which have told me that it had a problem recognizing the windows partitions and it have fixed that problem.

Then, indeed, w 7 repair disk have done anything more,  cause it told me that it wasn't be able to repair the w 7 startup, thought the tests have been mostly successful... And I have seen the date of the last known good configuration, so I have decided to try this startup option at the next reboot... And It works! Let's go to another quick reboot, just to see what happens with w vista...

The w vista  repair disk have found anything wrong with the vista startup, and Ihave decided to start vista by using the normal option this time. And it works too! 

I have stayed at the desktop a little longer, in order to do some tests (tdskiller, aswmbr, tdldetect, gmer -but I have stoped it soon this one- window defender, and the Avira boot sectors test), and it seems everythinf it's ok, except that I have found an error at aswmbr test. I don know what it's. *_Please, I would like someone to have a look at these screenshots_* and to tell me if the mbr is corect now.

[http://img42.imageshack.us/slideshow/webplayer.php?id=11211655.png](http://img42.imageshack.us/slideshow/webplayer.php?id=11211655.png)

Anyway, the main question is really solved: **ubuntu could clean up the mbr, and it could save and restore the partition table too, in a simple and easy way**.

Thank you again, mips, you led me into the right direction!

---

### Post by victux1 on 2011-04-20
I answer my own question.

Booting w 7 again, I find that asw.mbr is ok now. (Click.giftload was probably the guilty and it was fixed by SpybotS&D).

Now, the three OS are working well. I will folow using Av and anti-malware tools the next days, anyway.

My question about how to handle the mbr is solved. Ubuntu linux is so easy as useful.

Thanks for the guiding.

---

