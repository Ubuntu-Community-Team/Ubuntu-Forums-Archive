---
title: "open ssh? where/how to create a user/password?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by koloatree on 2008-01-01
hello,
i am working with a person from overseas and need her to have access to our development box. how can i create a user and password and once the person is logged in, have their view only in a certain directory? basically i need her to only to be able to edit files in /var/www/mysite/view directory and any subfolders in there.

any help would be greatly appreciated!

---

### Post by peitschie on 2008-01-01
Hi.

How vital is it that this person can't see other files/directories?

If it is critical that the person is only allowed to see files in the directory, you are looking for what is called an SSH chroot.  A reasonably good tutorial for this can be found here: [http://www.howtoforge.com/chrooted_ssh_howto_debian]("http://www.howtoforge.com/chrooted_ssh_howto_debian") and [http://debian.chains.ch/chroot/chroot.html]("http://debian.chains.ch/chroot/chroot.html")

If on the other hand, you don't mind the user being able to read/see other files (read only access), you can add a user, and set up the group permissions appropriately to allow them to only have write access on files in the specified directory.  I can provide more information on this if this option is desirable.

---

### Post by koloatree on 2008-01-01
hi, thanks for offering a helping hand!

i guess right now, i would prefer the easiest way. if the user can view files in my other diretories(photos, spreadsheets, etc), does that mean they can open them as well? 

thanks!

> **peitschie said:**
> Hi.

If on the other hand, you don't mind the user being able to read/see other files (read only access), you can add a user, and set up the group permissions appropriately to allow them to only have write access on files in the specified directory.  I can provide more information on this if this option is desirable.

---

### Post by koloatree on 2008-01-01
ok, i made some progress.

i added a user, assigned password, installed openssh, open the port, and all is dandy. however, i  may need help assigning the folder + subfolders to a user(or group) that they can write and execute. however, id like to make it so they cant execute or write anywhere else in the system.

thanks!

---

### Post by peitschie on 2008-01-01
Sounds like good work so far then.

Making it so they can't write anywhere else is straight forward.  By default, a user can only write to their home directory and /tmp.  Unless you explicitly give them access, they shouldn't be able to write anywhere else.

Unfortunately, most files are generally globally readable,  It is reasonably easy to change this however, but I would recommend reading a bit more before you decide how to do this.  I won't post the command just yet as running it could significantly impact your system!  (Any other linux guru's out there who can provide more help on this permissions bit would be appreciated)  Use google to look up linux file permissions... one that seems like a reasonable introduction is this one I found: [http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/) .  Have a read though, and this will help you understand what is and isn't possible :).  If this system is only being as a webserver for this one client, you may be safe simply revoking the everybody bit for read & execute access (something like chmod o-rwx I believe).   But as I said earlier, I don't know how safe this is and what further ramifications it could have on your system.

In answer to some of the other questions, if someone has read access to a file, it means they contents can be read but not modified, which means they **can open the file in a viewer or download the file (including photos, spreadsheets etc).**  Again, if this is a concern, you might want to use SSH chroot so the person logged in can't see your other directories.

---

### Post by koloatree on 2008-01-02
! HELP!!


ive made it through the tutorial 

[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

but i cant login via ssh?!

i get

/bin/bash: No such file or directory.

i tripled check the chrooted directory for bin and bash and its there.

also, i ran into an odd behavior. when executing the script i get 

cp: cannot stat `(0xffffe000)': No such file or directory
cp: cannot stat `(0xffffe000)': No such file or directory
cp: cannot stat `(0xffffe000)': No such file or directory
....

however, the programs are copied over to the chroot bin directory.?!?!?!?!?!?!?!?!?!?

Thanks for any help!

---

### Post by koloatree on 2008-01-02
i think i fixed the error message because i copied the for loop from this script

[http://www.howtoforge.com/forums/showthread.php?t=5942](http://www.howtoforge.com/forums/showthread.php?t=5942)

..however when i try to login, i still get the missing bin/bash yet they are there???


> **koloatree said:**
> ! HELP!!


ive made it through the tutorial 

[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

but i cant login via ssh?!

i get

/bin/bash: No such file or directory.

i tripled check the chrooted directory for bin and bash and its there.

also, i ran into an odd behavior. when executing the script i get 

cp: cannot stat `(0xffffe000)': No such file or directory
cp: cannot stat `(0xffffe000)': No such file or directory
cp: cannot stat `(0xffffe000)': No such file or directory
....

however, the programs are copied over to the chroot bin directory.?!?!?!?!?!?!?!?!?!?

Thanks for any help!

---

### Post by Dr Small on 2008-01-02
Just give them rbash, and they can't use cd and stuff.

---

### Post by koloatree on 2008-01-02
i also previously installed openssh, so maybe that could be the culprit?

---

### Post by peitschie on 2008-01-03
> **koloatree said:**
> 
...when executing the script i get 

cp: cannot stat `(0xffffe000)': No such file or directory
cp: cannot stat `(0xffffe000)': No such file or directory
cp: cannot stat `(0xffffe000)': No such file or directory
....

however, the programs are copied over to the chroot bin directory.?!?!?!?!?!?!?!?!?!?

This error is caused when copying the library files NOT the programs.

If you look at this snippet from the tutorial
```

        # obtain a list of related libraries
        ldd $prog > /dev/null
        if [ "$?" = 0 ] ; then
                LIBS=`ldd $prog | awk '{ print $3 }'`
                for l in $LIBS; do
                        mkdir -p ./`dirname $l` > /dev/null 2>&1
                        **cp $l ./$l**
                done
        fi
```
I have bolded the part that is generating that error.  Can you please post the output from running the following command in a shell/terminal:
```

APPS="/bin/bash /bin/ls /bin/mkdir /bin/mv /bin/pwd /bin/rm /usr/bin/id /usr/bin/ssh /bin/ping /usr/bin/dircolors"
for prog in $APPS;  do
        echo Copying $prog:

        # obtain a list of related libraries
        ldd $prog > /dev/null
        if [ "$?" = 0 ] ; then
                LIBS=`ldd $prog | awk '{ print $3 }'`
                for l in $LIBS; do
                        echo Library - $l
                done
        fi
done
```
This is getting a list of the libraries needed by each program, and should make it more transparent where the 0xffffe000 library name is coming from.  I did a quick google search and it seems your not the only one to get this problem doing chroot :-)

I suspect that because of the above error, the /bin/bash isn't functioning properly, so until we get this part fixed, don't worry about the other issues :)

Also, I noticed this forum thread may already have your solution: [http://ubuntuforums.org/showthread.php?t=128206](http://ubuntuforums.org/showthread.php?t=128206)

---

### Post by koloatree on 2008-01-03
hi, thanks for helping me! here is my output

Copying /bin/bash:
Library - (0xffffe000)
Library - /lib/libncurses.so.5
Library - /lib/tls/i686/cmov/libdl.so.2
Library - /lib/tls/i686/cmov/libc.so.6
Copying /bin/ls:
Library - (0xffffe000)
Library - /lib/tls/i686/cmov/librt.so.1
Library - /lib/libacl.so.1
Library - /lib/libselinux.so.1
Library - /lib/tls/i686/cmov/libc.so.6
Library - /lib/tls/i686/cmov/libpthread.so.0
Library - /lib/libattr.so.1
Library - /lib/tls/i686/cmov/libdl.so.2
Library - /lib/libsepol.so.1
Copying /bin/mkdir:
Library - (0xffffe000)
Library - /lib/libselinux.so.1
Library - /lib/tls/i686/cmov/libc.so.6
Library - /lib/tls/i686/cmov/libdl.so.2
Library - /lib/libsepol.so.1
Copying /bin/mv:
Library - (0xffffe000)
Library - /lib/libacl.so.1
Library - /lib/libselinux.so.1
Library - /lib/tls/i686/cmov/libc.so.6
Library - /lib/libattr.so.1
Library - /lib/tls/i686/cmov/libdl.so.2
Library - /lib/libsepol.so.1
Copying /bin/pwd:
Library - (0xffffe000)
Library - /lib/tls/i686/cmov/libc.so.6
Copying /bin/rm:
Library - (0xffffe000)
Library - /lib/tls/i686/cmov/libc.so.6
Copying /usr/bin/id:
Library - (0xffffe000)
Library - /lib/libselinux.so.1
Library - /lib/tls/i686/cmov/libc.so.6
Library - /lib/tls/i686/cmov/libdl.so.2
Library - /lib/libsepol.so.1
Copying /usr/bin/ssh:
Library - (0xffffe000)
Library - /lib/tls/i686/cmov/libresolv.so.2
Library - /usr/lib/i686/cmov/libcrypto.so.0.9.8
Library - /lib/tls/i686/cmov/libutil.so.1
Library - /usr/lib/libz.so.1
Library - /lib/tls/i686/cmov/libnsl.so.1
Library - /lib/tls/i686/cmov/libcrypt.so.1
Library - /lib/tls/i686/cmov/libc.so.6
Library - /lib/tls/i686/cmov/libdl.so.2
Copying /bin/ping:
Library - (0xffffe000)
Library - /lib/tls/i686/cmov/libresolv.so.2
Library - /lib/tls/i686/cmov/libc.so.6
Copying /usr/bin/dircolors:
Library - (0xffffe000)
Library - /lib/tls/i686/cmov/libc.so.6

---

### Post by peitschie on 2008-01-03
Okay.  Based on some more searching, it appears the cp (0xffffe000) errors can be reasonably safely ignored ([http://www.howtoforge.com/forums/archive/index.php/t-1739.html](http://www.howtoforge.com/forums/archive/index.php/t-1739.html)).

So, thats not the problem.

Are the copied files into the chroot directory executable?  Could you please post the output of running the following command from the chroot home directory:
```
ls -Rl
```

This will ensure all permissions on the copied files are set properly so the user who is going to log in can in fact execute the files.

---

### Post by koloatree on 2008-01-03
Greetings! it works! but i may of screwed something up.... :confused:

i deleted everything in the chroot directory that i created and started from scratch, this time following the debian etch tutorial?

[http://www.howtoforge.com/chroot_ssh_sftp_debian_etch](http://www.howtoforge.com/chroot_ssh_sftp_debian_etch)

i skipped step 2.1 in the new version which is

cd /tmp
apt-get install libpam0g-dev openssl libcrypto++-dev libssl0.9.7 libssl-dev ssh build-essential bzip2

wget [http://chrootssh.sourceforge.net/download/openssh-4.5p1-chroot.tar.bz2](http://chrootssh.sourceforge.net/download/openssh-4.5p1-chroot.tar.bz2)


in the original older version and what i currently have is

cd /tmp
 wget [http://www.zlib.net/zlib-1.2.3.tar.gz](http://www.zlib.net/zlib-1.2.3.tar.gz)

 apt-get install libpam0g-dev openssl libcrypto++-dev libssl0.9.7 libssl-dev ssh
wget [http://chrootssh.sourceforge.net/download/openssh-4.2p1-chroot.tar.gz](http://chrootssh.sourceforge.net/download/openssh-4.2p1-chroot.tar.gz)

so it seems that i am missing build-essential, bzip2, and the latest 4.5 openssh.



what shall i do?

thanks!

---

### Post by koloatree on 2008-01-03
in addition to, nano and pico doesnt work, i get

Error opening terminal: xterm

i found this using google, but dont know how to implement.


##############
I did follow that howto...I found my problem.

There needs to be a couple of xterm files from the etc dir in the folder. Here's how to add nano:

EDIT /root/ispconfig/scripts/shell/create_chroot_env.sh
ADD /bin/nano to the end of the APPS= line (before the last ")
ADD at the bottom:
#Allow nano to work
mkdir ./etc/terminfo/x/
cp /etc/terminfo/x/* ./etc/terminfo/x/

And viola!
##############

---

### Post by peitschie on 2008-01-03
Try
```

sudo apt-get install build-essential bzip2 openssh-server

```

---

### Post by peitschie on 2008-01-03
To fix the xterm thing, your not running a script, so simply change to the chroot dierctory and execute the following commands:

```

cp /bin/nano ./bin/nano
mkdir ./etc/terminfo/x/
cp /etc/terminfo/x/* ./etc/terminfo/x/

```

The fix you found is working on the original FOR-loop script you ran to set up the environment.

---

### Post by koloatree on 2008-01-03
thank you! everything is working!

for this:

sudo apt-get install build-essential bzip2 openssh-server

do i need to uninstall the old version? will things get messed?

thanks!

---

### Post by peitschie on 2008-01-03
> **koloatree said:**
> thank you! everything is working!

for this:

sudo apt-get install build-essential bzip2 openssh-server

do i need to uninstall the old version? will things get messed?

thanks!

I don't quite understand what you mean.  Which old version is being removed?

If everything is working as you say, I would leave it alone now :D

---

