---
title: "need to change menu title on grub2"
date: 2015-10-19
forum: Any Other OS
---

### Post by classacted on 2015-10-19
hello,


to be fair, I am letting it be known beforehand that I am posting this on other quality forums as well.  I hope I don't offend anyone and I will share all helpful info.


the problem:

need to change menu title on grub2.  to change this, I am supposed to edit the /etc/grub.d/30_os-prober file.  I can edit the /etc/grub.d/30_os-prober file, but as soon as I update grub and reboot, grub2 still shows **Microsoft Windows XP Professional (on /dev/sda1)**    my edit to the /etc/grub.d/30_os-prober file does not change, (it appears to be permanently saved, even after rebooting and updating grub2), yet it doesn't show on grub2 menu at boot.  anyone with suggestions or advice would be most appreciated.  **could I have a permissions issue, how would I check/verify?**

from the beginning:
when the computer boots up, first I get the bios splash screen, then I get the first grub screen.  listed among the entries is this:
**Microsoft Windows XP Professional (on /dev/sda1)**

I would rather have it say this:
**choose between XP Professional and tinycore**
below are highly regarded tutorials that show how to do it:
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[http://ubuntu-install.blogspot.com/2009/11/grub2-title-tweaks.html](http://ubuntu-install.blogspot.com/2009/11/grub2-title-tweaks.html)

both of these tutorials say the same thing.
1. Run this command to get the current Grub 2 menu entries:
sudo cat /boot/grub/grub.cfg | grep "menuentry" | cut -d '"' -f 2
2. This section appears around line 150 of the file. 
3. Copy the exact title you wish to change (Example: Microsoft Windows XP Home Edition ) and place it between the quotes in the first line below. Note the title does not include the portion "(on /dev/sdXX)"
Enter the desired title between the quotes in the second line below - in this example, "Windows XP" would replace "Enter Desired New Title Here".
--------------------------------------------------------------------------------------------------------------------------
[B]# if [ -z "${LONGNAME}" ] ; then
#    LONGNAME="${LABEL}"
# fi

  if [ "${LONGNAME}" = "Enter Exact Title You Just Copied" ] ; then
    LONGNAME="Enter Desired New Title Here"
  elif [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi[/B]
-----------------------------------------------------------------------------------------------------------------


here is what I did.  it is the exact edit in the 30_os-prober file:

-----------------------------------------------------------------------------------------------------------------

[B]#  if [ -z "${LONGNAME}" ] ; then
#    LONGNAME="${LABEL}"
#  fi


if [ "${LONGNAME}" = "Microsoft Windows XP Professional (on /dev/sda1)" ] ; then
  LONGNAME="choose between xp pro and tinycore"
elif [ -z "${LONGNAME}" ] ; then
  LONGNAME="${LABEL}"
fi[/B]

-----------------------------------------------------------------------------------------------------------------------

I have looked it over a dozen times.  I can't see where I have done anything wrong.  it appears to be correct.

there is more to the story, but I didn't think it was relevant and I didn't want to clutter the thread.  here is a link:
[http://reboot.pro/topic/20752-noobie-need-to-change-title-on-grub2-also-using-grub4dos-hd/](http://reboot.pro/topic/20752-noobie-need-to-change-title-on-grub2-also-using-grub4dos-hd/)

thank you

---

### Post by howefield on 2015-10-19
Thread moved to the "*Any Other OS*" forum.

---

### Post by oldfred on 2015-10-19
Best not to edit scripts, over the years the locations in different versions of grub2 change.

I prefer to copy boot stanza to 40_custom and then you can edit at will. Once you confirm it works ok, you then can turn off os-prober. If later you want to use os-prober to find a boot stanza for a new install just turn it back on.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[URL="https://help.ubuntu.com/community/Grub2/CustomMenus"]https://help.ubuntu.com/community/Grub2/CustomMenus
[/URL]
 One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.
[http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910](http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910)

   Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries or descriptions you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

If you want it first in grub menu make it 06_custom (do not add entries to both)

 or a new file that will be first in the menu
sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

      
 In /etc/default/grub I added this line for os-prober:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or 
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
or 
turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub[URL="https://help.ubuntu.com/community/Grub2/CustomMenus"]
[/URL]

---

### Post by classacted on 2016-04-25
hello,

below I have listed all of the feedback I received.  two lines accross indicates a different website, and one line represents a different reply on the same website.

a special thanks to old fred for his in-depth and well-organized reply.

I have decided that my time would be better spent learning more about grub4dos than grub2.  just my opinion.

I hope some person benefits from what is written here, and thanks to everybody.

----------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------

If you don't update Grub a lot, just manually enter the title you want in grub.cfg. Yes, if you run update-grub it will revert but...

As far as the code, the if test is obviously failing - perhaps there are trailing spaces in LONGNAME? I used to write a lot of code in XBase and the "$" operator was priceless. Rather than matching a string exactly, the $ operator looked to see if the text fragment was contained within the target... 

----------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------

Best not to edit scripts, over the years the locations in different versions of grub2 change.

I prefer to copy boot stanza to 40_custom and then you can edit at will. Once you confirm it works ok, you then can turn off os-prober. If later you want to use os-prober to find a boot stanza for a new install just turn it back on.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/Ma...tomGrub2Screen](https://help.ubuntu.com/community/Ma...tomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.
[http://askubuntu.com/questions/65952.../659910#659910](http://askubuntu.com/questions/65952.../659910#659910)

Copy the entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries or descriptions you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

If you want it first in grub menu make it 06_custom (do not add entries to both)

or a new file that will be first in the menu
sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup


In /etc/default/grub I added this line for os-prober:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
or
turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

----------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------

So i guess this seems obvious, but did you run grub-mkconfig after these changes?

----------------------------------------------------------------------------------------------------------

hello grail,

I have never heard of such a thing, so the answer is no.
thanks for the reply, and I will let you know if it works.

----------------------------------------------------------------------------------------------------------

Usually it would need to specify the target with -o :

grub-mkconfig -o /boot/grub/grub.cfg

----------------------------------------------------------------------------------------------------------

all "/etc/grub.d/30_os-prober" dose is tell " grub-mkconfig " HOW to make the " /boot/grub/grub.cfg " file

after you edit 30_os-prober you still have to make a NEW grub.cfg that reflects the changes you made

----------------------------------------------------------------------------------------------------------

Quote:
Usually it would need to specify the target with -o :

grub-mkconfig -o /boot/grub/grub.cfg
Yes, but the grub needs to be grub2, thus:
Code:

grub2-mkconfig -o /boot/grub2/grub.cfg

And this is for an MBR BIOS, not EFI.

----------------------------------------------------------------------------------------------------------


Quote:
Originally Posted by tomwest View Post
Yes, but the grub needs to be grub2
Depends on the distro. I have seen Centos with grub2, Ubuntu with grub.

----------------------------------------------------------------------------------------------------------

Change this
Code:

if [ "${LONGNAME}" = "Microsoft Windows XP Professional (on /dev/sda1)" ] ; then

to
Code:

if [ "${LONGNAME}" = "Microsoft Windows XP Professional" ] ; then

to get rid of (on /dev/sda1), in the section that looks like this
Code:

found_other_os=1
      onstr="$(gettext_printf "(on s)" "${DEVICE}")"
      cat << EOF
menuentry '$(echo "${LONGNAME} $onstr" | grub_quote)' --class windows --class os \$menuentry_id_option 'osprober-chain-$(grub_get_device_id "${DEVICE}")' {
EOF

change
Code:

onstr="$(gettext_printf "(on %s)" "${DEVICE}")"

to
Code:

onstr="$(gettext_printf "")"

----------------------------------------------------------------------------------------------------------

...in addition to what all others said,
Code:

# if [ -z "${LONGNAME}" ] ; then
# LONGNAME="${LABEL}"
# fi


if [ "${LONGNAME}" = "Microsoft Windows XP Professional (on /dev/sda1)" ] ; then
LONGNAME="choose between xp pro and tinycore"
elif [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

the logic is wrong. you're checking LONGNAME for the "microsoft windows..." string before it has been assigned to LONGNAME.
really it should look like this:
Code:

if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

if [ "${LONGNAME}" =~ *"Microsoft Windows XP Professional"* ] ; then
LONGNAME="choose between xp pro and tinycore"
fi

(i haven't tested the bit after '=~'. source)

----------------------------------------------------------------------------------------------------------

...in addition to what all others said,
Code:

# if [ -z "${LONGNAME}" ] ; then
# LONGNAME="${LABEL}"
# fi


if [ "${LONGNAME}" = "Microsoft Windows XP Professional (on /dev/sda1)" ] ; then
LONGNAME="choose between xp pro and tinycore"
elif [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

the logic is wrong. you're checking LONGNAME for the "microsoft windows..." string before it has been assigned to LONGNAME.
really it should look like this:
Code:

if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

if [ "${LONGNAME}" =~ *"Microsoft Windows XP Professional"* ] ; then
LONGNAME="choose between xp pro and tinycore"
fi

(i haven't tested the bit after '=~'. source)

----------------------------------------------------------------------------------------------------------


Quote:
Originally Posted by tomwest View Post
And this is for an MBR BIOS, not EFI.
Why not? Got EFI boot here and everything works fine...

----------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------

 Quote Originally Posted by ejames82 View Post
I have looked it over a dozen times. I can't see where I have done anything wrong. it appears to be correct.
No, it is not.
You should leave out the " (on /dev/sda1)" part.

From your own quote:
3. Copy the exact title you wish to change (Example: Microsoft Windows XP Home Edition ) and place it between the quotes in the first line below. Note the title does not include the portion "(on /dev/sdXX)"

----------------------------------------------------------------------------------------------------------



NB we have moved to BunsenLabs forums. (The Crunchbang forums will become read-only soon). You can register there and post your questions.

In this case I think you want to edit the title at the top of the grub screen? What you are trying to do is edit the titles of the menu entries (I'm not sure exactly)

To edit the grub theme, then have a read of Grub theme elements, and look for

    title-text    Specifies the text to display at the top center of the screen as a title.

---

### Post by oldfred on 2016-04-25
sudo update-grub is running the mkconfig. 

fred@Asusz97:~$ whereis update-grub
update-grub: /usr/sbin/update-grub /usr/share/man/man8/update-grub.8.gz
fred@Asusz97:~$ cat /usr/sbin/update-grub
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

And I have edited 40_custom exactly the same way with BIOS & UEFI. 
Although if UEFI boot the actual boot stanza may be different.

---

### Post by classacted on 2016-05-01
hello old fred,

to start with, I wish I would have made a video of the work I did.  then I could watch the video and jump right in and get caught up to where I left off.  the biggest issue for me is that I just don't have the time.  I work between 60 and 80 hours a week at my job and the one computer that is the best for this project (that I have on hand at the moment) takes over a half hour just to put in a spare hard drive for experimental purposes.  it's full of devices, the corsair power supply has lots of wires and the case is micro atx.  I have an atx computer at a friends that I need to get back from him which will be a much better choice to learn with.  it has lots of room and is of an older style which is much, much more friendly for this type of project.  I need to go with a winning situation from the start instead of the jammed up, chaotic mess that I have at this time.  in either case, however, I will be going with grub4dos instead of any version of grub.  it appears grub4dos has capabilities that grub does not.  about five years ago I was able to put a grub4dos hard drive in a case that already had a dual-boot hard drive and get it to work where I had access to four OS's.  there were a couple more screens of text with selections that needed to be made, but the functionability was there, and still is.  it has reliably worked for over five years and I wouldn't be surprised if it works for another five years.  here is a link if you want to know more about it.

[http://reboot.pro/topic/20752-noobie-need-to-change-title-on-grub2-also-using-grub4dos-hd/](http://reboot.pro/topic/20752-noobie-need-to-change-title-on-grub2-also-using-grub4dos-hd/)  

I have tried numerous times since then to patch in grub4dos hard drives, but they were all failures.  I really wish I would have made a video of what I did that day that I successfully installed that grub4dos with the grub2.  a good video with narration is priceless.

thanks again old fred.

---

### Post by oldfred on 2016-05-01
Grub4dos is older and will work on older systems.
It uses the same type of boot stanza as grub legacy, but I converted to grub2 6 years ago, so do not remember much.

Also since grub4dos not really maintained, I do not think it works with new UEFI systems, unless you want to boot in the old BIOS/Legacy/CSM boot mode.

---

