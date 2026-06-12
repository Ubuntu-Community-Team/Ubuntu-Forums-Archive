---
title: "New and Big problem already"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by confused44 on 2007-02-19
The following message appeared:

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

I haven't the foggy idea where to begin to fix this!! HELP PLEASE  :confused:

---

### Post by Maestro23 on 2007-02-19
> **confused44 said:**
> The following message appeared:

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

I haven't the foggy idea where to begin to fix this!! HELP PLEASE  :confused:

What version are you running first of all?  

Next, Open a terminal and type the following command.

> cat /etc/apt/sources.list

With your mouse, copy/paste the contents of the file here, so someone can begin to help you.

---

### Post by confused44 on 2007-02-19
I am running Ubuntu Desktop DC 6.06.

I don't even know HOW to open a terminal?  How do you do that?  Where are the instructions for things like that?  In HELP??

Thanks,

---

### Post by Vivix729 on 2007-02-19
Applications ->  Accessories ->  Terminal for opening the terminal.

---

### Post by jvc26 on 2007-02-19
Applications -> Accessories -> Terminal
Then type cat /etc/apt/sources.list
Copy the stuff from there into here.
Il

---

### Post by confused44 on 2007-02-19
THANKS SO MUCH.

Found terminal --

INPUT TEXT AND IT SAID:
]
mawf@mawf-desktop:~$ cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
mawf@mawf-desktop:~$

---

### Post by Vivix729 on 2007-02-19
You need a space between cat and /etc.

---

### Post by confused44 on 2007-02-19
THANKS AGAIN!!!!  I know nothing.  Re-entered with space and it worked!!! Thanks. 

Now it says:

mawf@mawf-desktop:~$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiver se
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ erse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

art manager

# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
mawf@mawf-desktop:~$

---

### Post by confused44 on 2007-02-19
I think the entry art manager --- I some how managed to get it in there and I think this is the problem  --- or 1 of them.  I was trying to find a file and now it's in this file and I know that always comes up as an error.

Thoughts?

---

### Post by jvc26 on 2007-02-19
Is that line 'art manager' in the file? If so: (In terminal)
```

gksudo gedit /etc/apt/sources.list

```
Enter your password
Remove the line from the sources.list (i.e. go to the back of the file and delete that line which says art manager at the bottom) then save and close the window.
(In terminal now: )
```

sudo apt-get update

```
Does that work?
Il

---

### Post by confused44 on 2007-02-19
I went in and deleted art manager.  but not sure it worked.  Got lost and confused.  Lastest says:


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by kelbizzle on 2007-02-19
Now open terminal again and type 
```
 sudo apt-get update 
```

---

### Post by confused44 on 2007-02-19
YES IT WORKED.  IT DID RESTORE THE ADD/REMOVE PROGRAMS FUNCTION...

Now will see if I can go on.

Thanks a million to you all!

I am confused and feel stupid but I am learning thanks to your help!!:KS

---

### Post by Maestro23 on 2007-02-19
> **confused44 said:**
> YES IT WORKED.  IT DID RESTORE THE ADD/REMOVE PROGRAMS FUNCTION...

Now will see if I can go on.

Thanks a million to you all!

I am confused and feel stupid but I am learning thanks to your help!!:KS

Some links you should read/bookmark:

Linux commands/File structure: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Installing in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
                              [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Restriced Formats(mp3, DVD): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

*Link to Ubuntu guide in my sig.

Good luck.

---

