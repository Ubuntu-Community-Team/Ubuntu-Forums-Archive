---
title: "Restart into another OS?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by sloopveedub on 2007-03-12
How can I set up the logoff menu to allow me to choose to restart automatically into a different operating system?  In Suse 10.2 (KDE), when I go to the "Leave" menu it gives me a bunch of options.  The usual ones are there: Log off, switch user, shut down, restart.  However, it also gives me the option to "restart into Windows."  If I select this option, it'll do just that -- reboot and automatically start Windows, so I don't have to sit there and wait for the GRUB menu, select windows manually.
:(

---

### Post by scxtt on 2007-03-12
my "guess" is that suse has 'tweaked' the logout menu in a way that it makes use of **grub-reboot**, which when issued can boot you into any menu entry in menu.lst ... there's no reason you can't issue that command yourself, instead of logging out in the more 'traditional' sense ...

---

### Post by igknighted on 2007-03-12
In fact you could make a button for the panel or a menu entry or a desktop icon with this command once you figure out what the proper one is, if you don't want to type it each time.

---

### Post by audax321 on 2007-03-12
Here is a script I wrote that you could use. I use it on my laptop to reboot to Windows.

Paste the code into a file called 'grub_reboot_to_os.sh' and make sure its executable:

```

#!/bin/sh

# Causes grub to reboot into OS specified by /boot/grub/menu.lst index.
# USAGE: sh grub_reboot_to_os.sh <index> <operating system description>
#   e.g. sh grub_reboot_to_os.sh 3 Windows XP Professional
#   Argument ordering must be exact!

num_argument=0
os_index=0
os_description="Default OS"

for argument in "$@"
do
	if [ "$num_argument" = "0" ]; then
		os_index="$argument"
	fi

	if [ "$num_argument" = "1" ]; then
		os_description="$argument"
	fi

	if [ "$num_argument" -gt "1" ]; then
		os_description=""$os_description" "$argument""
	fi
	
	num_argument=`expr $num_argument + 1`
done

if [ "$num_argument" = "1" ]; then
	os_description="Operating System #"$os_index""
fi

zenity --title="Confirmation" --question --text="Are you sure you wish to automatically load $os_description on the next reboot?"

if [ "$?" = "0" ]; then
	gksudo -m "Enter password for root access." -t "Got r00t?" "gnome-terminal -x /sbin/grub-reboot "$os_index"" &
fi

```

Then to load Windows, make a button/shortcut to the following:

sh /path/to/grub_reboot_to_os.sh <index> <name of OS>

e.g.

sh /path/to/grub_reboot_to_os.sh 3 Windows XP Professional

The script doesn't have to be run as root because it will ask you for root access at the appropraite time (the gksudo command in the script).

You determine the <index> by looking at the grub menu. The first item in the menu is 0, the next is 1, and so on. Put the number for the Windows entry here.

You could also write a script that does this more directly, but the reason I chose to do it this slightly complicated way is so if I for some reason install multiple operating systems, one script can be used to boot into any of them just be changing the arguments passed to the script.

Hope it helps.

---

