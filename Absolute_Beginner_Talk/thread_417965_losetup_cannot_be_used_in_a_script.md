---
title: "losetup cannot be used in a script?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by gizmomelb on 2007-04-22
Hi all,

fairly new ubuntu user here, but I'm having some help from a friend.

He's given me a script to run for me to set up some custom stuff on a USB flash disk (but he's currently offline for a while), but the script appears to be failing when it checks to see if the 'losetup' command is available.  'losetup' is there, I can run it fine from a console, but it just won't run in the script - any help on what needs to be changed would be most appreciated.

I've tried running the script as the current user, as 'sudo su' and as 'sudo su -' - all fail at the same point where the script checks to see if 'losetup' is available.  I believe he wrote the script using a Debian linux (?) and it works for him.

here is an extract from the script, with the failed section in bold:

[ "$(whoami)" = "root" ] || {
   echo "Warning - you don't seem to be root - this probably won't work...";
   sleep 4; 
   echo "Continuing anyway."
}

echo "Check that we can use losetup."
[B]losetup -a >/dev/null 2>/dev/null \
   || Fail 3 "Couldn't execute losetup - is it installed?"[/B]

echo "Check that we can use dd."
dd --version >/dev/null 2>/dev/null \
   || Fail 3 "Couldn't execute dd - is it installed?"

echo "Check that we can use mkfs.vfat"
which mkfs.vfat >/dev/null 2>/dev/null \
   || Fail 3 "Couldn't find mkfs.vfat"

echo "Check for a suitable version of echo."
[ -x /bin/echo ] \
   || Fail 3 "Couldn't find the desired version of echo" \
          "We're not picky, but we need a version which supports hex values" \
          "Edit this script if you know what to do..." \
          "(in the section that sets the partition type)"



any help on what I need to change the script/command to be so it'll work is most appreciated.

Regards,
Gizmomelb

---

### Post by bashologist on 2007-04-22
That's because there's no "-a" option available in ubuntu. Maybe it's available in debian. Tell him that then maybe he can fix it. Tell him "It says there's no -a option available".

It would have told you that kinda if he hadn't redirected the output...

---

### Post by gizmomelb on 2007-04-22
Hi,

thanks for the reply bashologist - I edited the script and removed the '-a' option but it still fails.

though if I comment out the "|| Fail 3 "Couldn't execute losetup - is it installed?"  it gets past it.

---

### Post by gizmomelb on 2007-04-22
hi all,

ok well there does seem to be some different options for the Debian version of 'losetup' as compared to the Ubuntu version of 'losetup'.  Is there any way to tell the version number of this commaned in each build, or is it because of different Kernel versions used etc?

The Debian version of losetup supports these options:

-a 
-s (value)

The Ubuntu version does'nt.

---

