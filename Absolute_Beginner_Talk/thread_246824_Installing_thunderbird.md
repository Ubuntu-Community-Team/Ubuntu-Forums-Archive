---
title: "Installing thunderbird"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-08-29
Lol sorry guys, I know im posting a lot today but how do I install thunderbird? I tried sudo apt-get install thunderbird but there was no luck with that.

---

### Post by Jagot on 2006-08-29
```
sudo aptitude update
sudo aptitude install mozilla-thunderbird
```

---

### Post by Toxicity999 on 2006-08-29
For future reference synaptic is your friend when you don't know the full name of the package, easier than command based searches if your new. A qucik search for thunderbird would of given you what you needed.

---

### Post by Narcoleptic_Insomniac on 2006-08-29
What is synaptic and it gave me this when I tried what the guy above toxicity said 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

---

### Post by Jagot on 2006-08-29
Synaptic is a graphical package management front-end for apt-get.

Now, do as it says:

```
sudo dpkg --configure -a
```

---

### Post by Narcoleptic_Insomniac on 2006-08-29
It says

dpkg: requested operation requires superuser privilege

when I do the dpkg thing you said. I assume this means I have to give my password or something but it doesnt show that option.

---

### Post by Jagot on 2006-08-29
Run it with sudo as I put in my previous post:

```
sudo dpkg --configure -a
```

---

### Post by Narcoleptic_Insomniac on 2006-08-29
Nothing happened lol.

---

### Post by Jagot on 2006-08-29
OK, well now try and install thunderbird again:

```
sudo aptitude update
sudo aptitude install mozilla-thunderbird
```

---

### Post by Anonii on 2006-08-29
_"dpkg --configure -a"_

gives you: **dpkg: requested operation requires superuser privilege**

and _"sudo dpkg --configure -a"_

**gives you nothing?**

Thats not normal. Please paste the output of these commands here.

Also test: *"sudo ls"*
just to be sure that your sudo is not broken :/

---

### Post by Narcoleptic_Insomniac on 2006-08-29
And it gives me this

The following NEW packages will be installed:
  mozilla-thunderbird
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.3MB/15.0MB of archives. After unpacking 29.3MB will be used.
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)' in the drive '/cdrom/' and press enter

aptitude: download_signal_log.cc:67: virtual bool download_signal_log::MediaChange(std::string, std::string): Assertion `rval != -1' failed.
Aborted

Sorry I don't know this stuff.

---

### Post by Anonii on 2006-08-29
> **Narcoleptic_Insomniac said:**
> And it gives me this

The following NEW packages will be installed:
  mozilla-thunderbird
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.3MB/15.0MB of archives. After unpacking 29.3MB will be used.
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)' in the drive '/cdrom/' and press enter

aptitude: download_signal_log.cc:67: virtual bool download_signal_log::MediaChange(std::string, std::string): Assertion `rval != -1' failed.
Aborted

Sorry I don't know this stuff.

Open your terminal, and type:
*sudo gedit /etc/apt/sources.list*

Find a line which _DOESNT_ start with "#" and says something about that CDrom. Find that, and put a "#" in front of this line. Then try again.

If you dont understand that, please copy-paste your /etc/apt/sources.list here!

Good Luck :)

---

### Post by Narcoleptic_Insomniac on 2006-08-29
> **Anonii said:**
> Open your terminal, and type:
*sudo gedit /etc/apt/sources.list*

Find a line which _DOESNT_ start with "#" and says something about that CDrom. Find that, and put a "#" in front of this line. Then try again.

If you dont understand that, please copy-paste your /etc/apt/sources.list here!

Good Luck :)

So all kinds of lines dont start with # so I didnt touch it cause I don't know what to do lol.. heres the whole thing.


deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Whats wrong with it.

---

### Post by Jagot on 2006-08-29
Here's a nice sources.list.  Copy and paste it to replace yours:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free 
```

---

### Post by Narcoleptic_Insomniac on 2006-08-29
This also came up after I type the sudo thing to open up all that...

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

Any help?

---

### Post by Anonii on 2006-08-29
Even if you got these errors, the window with the Text Editor opened?
If it opened, you can proceed, it wont alter your configurations afaik. I had this problem too. I advise you tho, to try to fix it after you fix this Thunderbird problem :)

After updating your sources.list with the one Jober gave you. Run:
[I][U]
sudo aptitude update
sudo aptitude install mozilla-thunderbird[/U][/I]

---

### Post by Narcoleptic_Insomniac on 2006-08-29
> **Jagot said:**
> Here's a nice sources.list.  Copy and paste it to replace yours:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free 
```


Well I did that and now when I type sudo aptitude update I get 

E: Type 'ALSA' is not known on line 1 in source list /etc/apt/sources.list
E: Type 'ALSA' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by Anonii on 2006-08-29
> **Narcoleptic_Insomniac said:**
> Well I did that and now when I type sudo aptitude update I get 

E: Type 'ALSA' is not known on line 1 in source list /etc/apt/sources.list
E: Type 'ALSA' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Try :

*sudo aptitude update*

before that command :]

---

### Post by Narcoleptic_Insomniac on 2006-08-29
> **Anonii said:**
> Try :

*sudo aptitude update*

before that command :]

I typed sudo aptitude update and thats what I got, but I tried again just to make sure and got the same thing

---

### Post by Narcoleptic_Insomniac on 2006-08-29
Ok wwell, I tried sudo aptitude install mozilla-thunderbird again, and it sort of worked, but it installed Evolution again. Lol. But I can always just purge my comp of it again, or should I not do that.

---

### Post by Toxicity999 on 2006-08-29
did you somehow accidently paste that ALSA error output in you Sources.list? ;) You must of. And don't bother removing Evolution... it's better just to remove the links for simplicities sake otherwise a few minor things break. Unless you're desperate for space, by all means it won't break anything useful.

---

