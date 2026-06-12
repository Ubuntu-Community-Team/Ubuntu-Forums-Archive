---
title: "Howto disable automatic dialup at boot time?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by 299 on 2006-10-23
Hello, i am using Ubuntu 5.10 and have followed the instructions in the
DialupModemHowto
 [https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

 to compile and install a driver for my Intel536EP modem.

The modem works well now and i have no problems connecting to to Internet.

The connection to my ISP is automaticly activated at boot time, before login,
i want to disable the automatic connection, but i dont know which instruction
to leave out from the howto.

I am pasting here a copy of part of the howto:
---------------------------------------------

Installing the driver

    *

      There are two steps to installing the driver. The first is to copy the Intel536.ko file created above to an appropriate directory, and the second is to cause the driver to be loaded at boot time.

      Installing the Intel536.ko file

      Copy the file to the modules directory by this command:

 sudo cp Intel536.ko /lib/modules/$(uname -r)/kernel/drivers/char

      You may be prompted for a password; if so, enter your user password.

      Make your system aware of this module with depmod:

 sudo depmod -a

      Finally, load the driver with the modprobe command:

 sudo modprobe Intel536

      This command should not print a response; if it prints something like this:

 FATAL: Module Intel536 not found.

      you have made an error; most likely you have copied the file to the wrong place. If you see a different error message, there may be an error in the module, or your modem, or you may not have a Intel 536-based modem.

      Loading the driver at boot time

      To load the module at boot time, we need to add a line "Intel536" to the file /etc/modules. First make a backup of the file:

 sudo cp /etc/modules /etc/modules.backup

      Now add the required line as follows:

 sudo sh -c "echo Intel536 >> /etc/modules"

Using the modem

    *

      The name of your modem device is /dev/536ep0. You can now use

sudo pppconfig to set up pon & poff. To use Kppp you will need to create a symlink be able to link the /dev/536ep0 to /dev/modem. Udev rewrites the /dev on each reboot and you thus have to create a file /etc/udev/rules.d/10-local.rules and put the following lines in it:

    *

 # Intelmodem536ep
 KERNEL="536ep0" SYMLINK="modem"

Now reboot and you can use Kppp to query the modem as this is a quick check if all is well before dialling out. Configure KPP for your ISP connection. These Intel modems are found to be more stable and less finicky that the Smartlink types on Breezy.
------------------------------------

Thanks for any help anyone can offer
:???:

---

