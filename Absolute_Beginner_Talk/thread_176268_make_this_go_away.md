---
title: "make this go away"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by isniffcorn on 2006-05-14
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)



this comes up when i open up snyaptic package manager, i'm not using the cdrom for packages (i dont even know where mine is to be honest :)). so how do i stop this from coming up

---

### Post by DSn0wMan on 2006-05-14
You just need to remove the cdrom repository from synaptic.

give me a sec, and I will provide detailed instruction.

---

### Post by cgjones on 2006-05-14
If you could, post the contents of /etc/apt/sources.list so we can see what is going on.

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=DSn0wMan]You just need to remove the cdrom repository from synaptic.

give me a sec, and I will provide detailed instruction.[/QUOTE]

Oops, I think I was wrong. Because I have the CD repository there, and it dosn't complain. 

Please post /etc/apt/sources.list

---

### Post by isniffcorn on 2006-05-14
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by DSn0wMan on 2006-05-14
That actually looks good to me. Maybe someone else can see something I cant.

When my synaptic was complaining (same errors as you have) I did the following commands to fix it.

sudo apt-get update
sudo apt-get upgrade

no more complaints.

edit: you will need to close synaptic for this to work.

---

### Post by Kvark on 2006-05-14
Comment (add a # in front of) the line that says cdrom to prevent apt-get from searching there. It can't complain about or ask for the CD if it doesn't look for it.

While you're at it, uncomment (remove the # in front of) all other lines with urls to make apt get search the entire repositories and find as many programs as possible.

So when you are done the file should look like this:
```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://us.archive.ubuntu.com/ubuntu/ breezy universe
```

And do "sudo apt-get update" after saving to make apt-get use the new file.

---

### Post by isniffcorn on 2006-05-14
[QUOTE=DSn0wMan]That actually looks good to me. Maybe someone else can see something I cant.

When my synaptic was complaining (same errors as you have) I did the following commands to fix it.

sudo apt-get update
sudo apt-get upgrade

no more complaints.

edit: you will need to close synaptic for this to work.[/QUOTE]

E: Some index files failed to download, they have been ignored, or old ones used instead.
that's the one i got when i did sudo update

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

that's what i got when i ran upgrade.
the good news is the errors when i open are down to those 2 couldnt stat source, iinstead of the original 4 heh

---

### Post by uzi09 on 2006-05-14
do you mind putting the breezy install cd in the cd rom and running whatever you ran to get this error again?

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=Kvark]Comment (add a # in front of) the line that says cdrom to prevent apt-get from searching there. It can't complain about or ask for the CD if it doesn't look for it.[/QUOTE]

I think Kvark has the best solution. I can't see any reason to have it use the CD rom as a repository. The only thing is that for some reason my synaptic does have the cd rom listed, but doesn't care that it's not in the computer.

---

### Post by isniffcorn on 2006-05-14
hey thanx man. it took me a bit of time to figure out how to edit the text file, my buddy is like use sudo.
i'm used to windows :-/
thanks a lot tho

---

### Post by isniffcorn on 2006-05-14
thanks a lot kvark it worked, it took me a while to figure out how to edit, then my buddy said use sudo. i'm used to windows ya know :-/

and uzi09 i would gladly do that if i knew where my cdrom was :)

whoops sorry i just totally double posted :(

---

### Post by uzi09 on 2006-05-14
sounds like it worked. so you're saying you just had to run the command with "sudo" and it did the trick??

please let us know what the solution was so that if someone else has a similar problem and comes across this thread, they also have the solution :D

EDIT: oops, i was in the middle of writing this and got distracted - by the time i submitted, u had already posted :S

---

### Post by isniffcorn on 2006-05-14
well first you gotta change your directory
so you do
**cd /etc/apt**
after that you do
**sudo gedit sources.list**
then you do exactly as kvark said
put a # in front of deb cdrom, it should look just liked this
[B]# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


[/B]

---

