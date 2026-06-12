---
title: "Got to get this fixed tonight!!!"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by jasonhr on 2007-09-09
I have dual booted our works server so that we can use linux to share files instead of wi***ws 2000 server.

I made it dual boot because that way if there is anything in the hardware that doesn't work I could go back.

My problem is that in the current configuration the Wi***ws server has all its user files on a separate disk. 

I have tried many tutorials to move the /home folder to the second disk and most of them fall over half way through leaving me unsure of where I am to try again.

So far I have done this:

$mkdir /mnt/newhome
$sudo mount -t ntfs /dev/hdb1 /mnt/newhome

then this:

$cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/

but the cpio bit falls over saying that -d is an invalid option

As you can see the second disk is still formatted in NTFS and I would like it to stay that way if I can.

please can someone help me out before I get sacked and probably beaten to death.

:confused:

---

### Post by jasonhr on 2007-09-09
OK, got his far...

 find . -depth -print0 | sudo cpio --null --sparse -pvd /mnt/newhome
cpio: cannot make directory `/mnt/newhome/./jason': Read-only file system
cpio: /mnt/newhome/./jason/.sudo_as_admin_successful: No such file or directory
cpio: cannot make directory `/mnt/newhome/./jason': Read-only file system
cpio: /mnt/newhome/./jason/.Xauthority: No such file or directory
cpio: cannot make directory `/mnt/newhome/./jason': Read-only file system
cpio: /mnt/newhome/./jason/.gstreamer-0.10/registry.i486.xml: No such file or directory
cpio: cannot make directory `/mnt/newhome/./jason': Read-only file system
cpio: /mnt/newhome/./jason/.gstreamer-0.10: No such file or directory
cpio: cannot make directory `/mnt/newhome/./jason': Read-only file system
cpio: /mnt/newhome/./jason/.metacity/sessions/1189360128-6039-1039329576.ms: No such file or directory
cpio: cannot make directory `/mnt/newhome/./jason': Read-only file system
cpio: /mnt/newhome/./jason/.metacity/sessions/1189359216-5728-1104574523.ms: No such file or directory


How can I make this writeable? I know it's a chown thing but I have never done any of this before.  I will keep trying to plug through this but some help would be really appreciated!

---

### Post by alienexplorers on 2007-09-09
If your second disk "newhome" is NTFS then you need ntfs-3g to write to it.
If "newhome" is ext3 then you need to use chown:
> terminator@terminator-desktop:~$ chown --help
Usage: chown [OPTION]... [OWNER][:[GROUP]] FILE...
  or:  chown [OPTION]... --reference=RFILE FILE...
Change the owner and/or group of each FILE to OWNER and/or GROUP.
With --reference, change the owner and group of each FILE to those of RFILE.

  -c, --changes          like verbose but report only when a change is made
      --dereference      affect the referent of each symbolic link, rather
                         than the symbolic link itself (this is the default)
  -h, --no-dereference   affect each symbolic link instead of any referenced
                         file (useful only on systems that can change the
                         ownership of a symlink)
      --from=CURRENT_OWNER:CURRENT_GROUP
                         change the owner and/or group of each file only if
                         its current owner and/or group match those specified
                         here.  Either may be omitted, in which case a match
                         is not required for the omitted attribute.
      --no-preserve-root do not treat `/' specially (the default)
      --preserve-root    fail to operate recursively on `/'
  -f, --silent, --quiet  suppress most error messages
      --reference=RFILE  use RFILE's owner and group rather than
                         the specifying OWNER:GROUP values
  -R, --recursive        operate on files and directories recursively
  -v, --verbose          output a diagnostic for every file processed

The following options modify how a hierarchy is traversed when the -R
option is also specified.  If more than one is specified, only the final
one takes effect.

  -H                     if a command line argument is a symbolic link
                         to a directory, traverse it
  -L                     traverse every symbolic link to a directory
                         encountered
  -P                     do not traverse any symbolic links (default)

      --help     display this help and exit
      --version  output version information and exit

Owner is unchanged if missing.  Group is unchanged if missing, but changed
to login group if implied by a `:' following a symbolic OWNER.
OWNER and GROUP may be numeric as well as symbolic.

Examples:
  chown root /u        Change the owner of /u to "root".
  chown root:staff /u  Likewise, but also change its group to "staff".
  chown -hR root /u    Change the owner of /u and subfiles to "root".


---

