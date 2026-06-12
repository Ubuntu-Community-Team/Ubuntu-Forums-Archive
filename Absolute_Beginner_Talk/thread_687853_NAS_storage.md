---
title: "NAS storage"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by sundance2007 on 2008-02-04
Can the Netgear SC101 NAS device be use with Linux and a PC to have a common storage area?

If so where do I look for beginner directions for setting this up?

Thanks

---

### Post by jmar71n on 2008-02-04
You should be able to mount the SMB shares, so they look like an ordinary hard drive. 

You will need to install smbfs 
#** sudo apt-get install smbfs**

Then edit fstab to mount the shares, and create a mount point

# **sudo gedit /etc/fstab**

Do a search for mounting samba shares + fstab to find out how to do this.
a few to get you started :)

[http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares]("http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares")

[http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/]("http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/")

---

### Post by guillemsola on 2008-02-07
Hi,

I worked with one of this and I think that SC101 is not a NAS device. It is a SAN device that uses its own software and there is no linux version.

wishes

---

### Post by sundance2007 on 2008-02-07
> **angrychai said:**
> Hi,

I worked with one of this and I think that SC101 is not a NAS device. It is a SAN device that uses its own software and there is no linux version.

wishes


You are correct,  I don't think the SC101 will work. I didn't ask about the SC101, I was just looking for general information and the links in the first reply I think give one just about everything  they need to do this.

I do have another question. There was great information on how to do this but I didn't see what device was being used to connect the drives to the network unless I just missed this.

Also, will this device be available to my Mac and PC as well?

Thanks

---

### Post by magicfab on 2008-06-13
Works fine in Hardy for me with the nbd module. See:
[http://ubuntuforums.org/showpost.php?p=4151832&postcount=15](http://ubuntuforums.org/showpost.php?p=4151832&postcount=15)

If you'd like to know if/when this makes it into Ubuntu, please subscribe to this bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/213744](https://bugs.edge.launchpad.net/ubuntu/+bug/213744)

Cheers,

---

### Post by cacycleworks on 2008-06-14
> **jmar71n said:**
> You should be able to mount the SMB shares, so they look like an ordinary hard drive. 

You will need to install smbfs 
#** sudo apt-get install smbfs**

Then edit fstab to mount the shares, and create a mount point

# **sudo gedit /etc/fstab**

Do a search for mounting samba shares + fstab to find out how to do this.
a few to get you started :)

[http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares]("http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares")

[http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/]("http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/")

Oh cool... maybe this can help a little bit. My office is a mixed Win/Linux environment as I'm working on our transition away from windows. I use smbfs but have not bothered with fstab and instead have a more flexible solution.

I wrote this bash script to allow the immediate mounting of any windows share via the command line. Basically, I needed to be able to move, copy, edit files across our network and smbfs gives linux a powerful tool! 

One of our shares is the most common used, so I created a default section in the script. I have used this script for a year and it serves me well. 

```

02:24 chris@outside ~/bin$ cat smb
#!/bin/bash
#
if [ ! $1 ]; then
        echo ""
        echo "./smb <-m|-u> [//win/share/] [-user user -pass pass]"
        echo ""
        echo " whatever.... "
        echo ""
        exit 1
fi

#
# arg parse from: http://www.digitalpeer.com/id/parsing
#
while [ $# -gt 0 ]; do
    case $1 in
        -m)
            MOUNT=1
            shift
            ;;
        -u)
            MOUNT=0
            shift
            ;;
        -user)
            LOGIN=$2
            shift 2
            ;;
        -pass)
            PASS=$2
            shift 2
            ;;
        --)
            shift
            break
            ;;
        *)
                if [ `echo $1 | grep "/"` ]; then
                        FOO=(`echo $1 | tr '/' ' '`)
                        WIN="${FOO[0]}"
                        SHARE="${FOO[1]}"
                else
                        echo "Option processing error: $1 unknown" 1>&2
                        exit 1
                fi
                shift
            ;;
    esac
done

if [ "${LOGIN}" ]; then
        LOGIN="username=$LOGIN"
fi
if [ "${PASS}" ]; then
        PASS="password=$PASS"
else  # to allow for default insertion of password
        PASS="password=yourPASS"
fi
if [ "${PASS}" ] && [ "${LOGIN}" ]; then
        OPTIONS="-o $LOGIN,$PASS"
else
        OPTIONS="-o $LOGIN $PASS"
fi

# this area can be used for default options
if [ ! "${WIN}" ]; then
        WIN=computerName
        SHARE=share
        PASS="password=yourPASS"
        OPTIONS="-o $PASS"
fi
# echo "\$OPTIONS = $OPTIONS"
if [ $MOUNT -eq 1 ]; then
        [ ! -d ${WIN} ] && mkdir ${WIN}
        smbmount //${WIN}/${SHARE} $WIN $OPTIONS # 2>/dev/null
        echo "//${WIN}/${SHARE} mounted at ./$WIN"
else
        smbumount $WIN
        rmdir $WIN
fi

exit 0

02:24 chris@outside ~/bin$

```

---

### Post by jhenager on 2008-06-14
> **jmar71n said:**
> 
[http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/]("http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/")

This link was the most helpful, once I copied and pasted the text into an editor so I could read it. (Worst possible choice of text/background color on a webpage).

Here is the entry in fstab:
//192.168.15.101/Jeff /media/Storage cifs auto,iocharset=utf8,uid=jeff,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

cifscredentials file is exactly as in the article. Works great.

---

### Post by jhenager on 2008-06-15
Ok, now, a day later, and having made no changes it no longer works.
I can ping the NAS device.
No folders were changed on the NAS device.
I get "mount error 20 = Not a directory".
Directory does exist.
jeff@jeff-desktop:~$ ls -al /media
total 16
drwxr-xr-x  4 root root 4096 2008-06-15 08:09 .
drwxr-xr-x 22 root root 4096 2008-06-14 10:23 ..
lrwxrwxrwx  1 root root    6 2008-02-13 17:37 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-02-13 17:37 cdrom0
-rw-r--r--  1 root root    0 2008-06-15 08:09 .hal-mtab
-rw-------  1 root root    0 2008-06-15 08:04 .hal-mtab-lock
drwxrwxr-x  2 root root 4096 2008-06-14 08:53 Storage

I'm stumped. This shouldn't be this hard.

---

