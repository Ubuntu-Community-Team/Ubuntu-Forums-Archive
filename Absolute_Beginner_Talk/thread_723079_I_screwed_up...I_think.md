---
title: "I screwed up...I think"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by i_have_a_sempron on 2008-03-13
I was reading an interesting blog about cracking wep keys...And I believe I did something very stupid. These are the terminal commands and actions I performed.

    sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
    sudo gedit /etc/apt/sources.list

While in the editor, replace everything with:

    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
    deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free


--------------------------------------------------------------------------------------------------------------------------------
If someone could help me get my settings correct, I will never do something this stupid again.

---

### Post by jan quark on 2008-03-13
what exactly does not work ?

---

### Post by kpkeerthi on 2008-03-13
Did you run any commands after changing sources.list? like sudo aptitude update/upgrade. If not just restore the file back from the backup you made (sources.list_backup)

---

### Post by i_have_a_sempron on 2008-03-13
After all that I ran

sudo apt-get update

After that I also ran installs

sudo apt-get install build-essential
sudo apt-get install aircrack
sudo apt-get install kismet
sudo apt-get install airsnort
sudo apt-get install linux-source
sudo apt-get install linux-headers
sudo apt-get install sharutils

Then I went to update Ubuntu and only got a partial update. My boot up time is now about 20 minutes...I'm not going to be doing this ever again lol.

---

### Post by kpkeerthi on 2008-03-13
Oops! Is this all on gutsy? You may try restoring sources.list from backup and then do 
**sudo aptitude update && sudo aptitude dist-upgrade** again.

But I'm not sure if you'll get back gutsy in proper shape. Worth a try before you do a reinstall.

---

### Post by i_have_a_sempron on 2008-03-13
Sorry for asking lame questions but how do I run the restore backup?

---

### Post by i_have_a_sempron on 2008-03-13
Alright I put in:

restore source.list

And I was prompted to 

sudo apt-get install dump

I was able to get that then ran the restore command again and this is what I got back

restore: option requires an argument -- s
restore 0.4b41 (using libext2fs 1.40.2 of 12-Jul-2007)
usage:  restore -C [-cdHlMvVy] [-b blocksize] [-D filesystem] [-f file]
                   [-F script] [-L limit] [-s fileno]
        restore -i [-acdhHlmMouvVy] [-A file] [-b blocksize] [-f file]
                   [-F script] [-Q file] [-s fileno]
        restore -P file [-acdhHlmMuvVy] [-A file] [-b blocksize]
                   [-f file] [-F script] [-s fileno] [-X filelist] [file ...]
        restore -r [-cdHlMuvVy] [-b blocksize] [-f file] [-F script]
                   [-s fileno] [-T directory]
        restore -R [-cdHlMuvVy] [-b blocksize] [-f file] [-F script]
                   [-s fileno] [-T directory]
        restore -t [-cdhHlMuvVy] [-A file] [-b blocksize] [-f file]
                   [-F script] [-Q file] [-s fileno] [-X filelist] [file ...]
        restore -x [-acdhHlmMouvVy] [-A file] [-b blocksize] [-f file]
                   [-F script] [-Q file] [-s fileno] [-X filelist] [file ...]

---

### Post by Arthur Archnix on 2008-03-13
First, do you have Gutsy? In a terminal type: ```
uname -r
```EDIT: And I just noticed that the instructions you followed made you make a backup of your sources. So just do:
```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```Then,
```
 sudo apt-get update
```I'm confused about upgrade and dist-upgrade in these situations, so I'll let others weigh in on the next command to run.

---

### Post by Tatty on 2008-03-13
What you seem to have done is changed all of the repos to Dapper repos.  If you use gutsy  that would almost definately break your system.

to restore your backup sources file simply reverse the copy command you issues earlier, so according to what you said you did earlier you need to do:

```
cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

---

### Post by i_have_a_sempron on 2008-03-13
After 

uname -r

I got 

2.6.22-14-generic

After

cp /etc/apt/sources.list_backup /etc/apt/sources.list

I recieved

cp: cannot create regular file `/etc/apt/sources.list': Permission denied

---

### Post by Arthur Archnix on 2008-03-13
Because you need sudo

---

### Post by kpkeerthi on 2008-03-13
Yes.. you need to run these commands in the order
```

sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list

```
```
sudo aptitude update
```
```
sudo aptitude dist-upgrade
```

---

### Post by i_have_a_sempron on 2008-03-13
After running 

sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list

I get no response in Terminal. Am I entering it incorrectly?

---

### Post by kpkeerthi on 2008-03-13
Yes. Just run the next two commands.

---

### Post by i_have_a_sempron on 2008-03-13
Awesome so far everything is running a bit better. Haven't checked the boot time yet, but any ideas on how to speed that up?

---

### Post by kpkeerthi on 2008-03-13
System -> Admin -> Services and turn off those that are not need. But be very careful doing this. It is usually safe to turn off 
bluetooth - if you do not have any bluetooth devices. 
cups service - if you do not use printer. 
screen - you may not need this also

Be cautious with rest of the services.

---

### Post by Arthur Archnix on 2008-03-13
The next time you boot go into grub where you choose between boot options like Ubuntu, Recovery and Memtest. Highlight Ubuntu and press 'e'. Then highlight the kernel line and press 'e'. Then go to the end of the line, add a space after the last entry and type "profile" without quotes. Hit enter. Then press 'b'.

This one boot will take much longer, but after that you should notice an improvement in boot speed.

---

### Post by i_have_a_sempron on 2008-03-13
Well thank you all for the help...Im going to refrain from doing any more random, idiotic ideas lol. Other than just this forum, where are some decent places to learn basic linux functions?

---

### Post by kpkeerthi on 2008-03-13
Check out the links in my signature.

---

### Post by i_have_a_sempron on 2008-03-13
Will do. Went into grub and added Profile on to the end of the kernel line, haven't noticed a speed increase yet but i'll be sure to keep trying. Thank you all.



Maybe I should get a new cpu...Sempron might have gone out of date....lmao

---

