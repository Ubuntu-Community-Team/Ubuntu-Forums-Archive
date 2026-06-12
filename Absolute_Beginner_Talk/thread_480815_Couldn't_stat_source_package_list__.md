---
title: "Couldn't stat source package list? ?_?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-06-21
Whenever I try to update (via apt-get, for example), I see a bunch of errors about how I don't have files/directories...

> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


^That's what I'm seeing...am I missing something important and if so, how do I find/fix it?

---

### Post by NeoLithium on 2007-06-21
Can you open up a terminal window and copy and paste the output of this command:
```
cat /etc/apt/sources.list 
```

We'll get it figured out for ya :)

---

### Post by ARandomKid on 2007-06-21
> #See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
#newer versions of the distribution

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT recieve any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT recieve any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT recieve any review
## or updates from the Ubuntu security team.
 deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse
 deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security multiverse
[B]deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) etch main[/B]

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse


Not sure why the getautomatix.com things are in there (bolded)...they don't seem to be relating to my version of ubuntu (not breezy like the rest of the links, but rather dapper/etch), nor do I have automatix installed...odd.

Should I leave those in or just delete them?

---

### Post by NeoLithium on 2007-06-21
I just realized what it was. Hopefully someone will correct me quick if I'm wrong, but I believe that the breezy repositories are all down because the support time has ended for it. You'll have to look into upgrading to Dapper, Edgy or Feisty :)

---

### Post by ARandomKid on 2007-06-21
Yea, that would make sense.

I've been trying to upgrade to Dapper for a while now, but can't seem to find a computer in my house that wants to burn the iso...all the cd burners don't want to work right. ;>_<

And the one computer that I know can burn correctly was fried last month...

so it might take a while...but that's nothing you can really help out with.

But thanks for helping me out on this issue! It's been puzzling me for some time...

---

### Post by jfinkels on 2007-06-21
> **ARandomKid said:**
> Yea, that would make sense.

I've been trying to upgrade to Dapper for a while now, but can't seem to find a computer in my house that wants to burn the iso...all the cd burners don't want to work right. ;>_<

And the one computer that I know can burn correctly was fried last month...

so it might take a while...but that's nothing you can really help out with.

But thanks for helping me out on this issue! It's been puzzling me for some time...

All you need to do to upgrade to the next higher version of Ubuntu is type the following command:```
gksudo update-manager -c
```

---

### Post by NeoLithium on 2007-06-21
Well, if downloading and burning isn't your thing, you can always check out [http://shipit.ubuntu.com](http://shipit.ubuntu.com) and order the discs, it will take a few weeks, but if that's faster than getting a new burner; could be worth it.  Generally, using the update manager to upgrade is the preferred method to do it, though if you have a slower connection it could be....well, annoying to say the least.  Just ensure if you want to try to do that with the update manager, that you comment out the automatix repositories first.

---

### Post by jfinkels on 2007-06-21
> **NeoLithium said:**
> Well, if downloading and burning isn't your thing, you can always check out [http://shipit.ubuntu.com](http://shipit.ubuntu.com) and order the discs, it will take a few weeks, but if that's faster than getting a new burner; could be worth it.  Generally, using the update manager to upgrade is the preferred method to do it, though if you have a slower connection it could be....well, annoying to say the least.  Just ensure if you want to try to do that with the update manager, that you comment out the automatix repositories first.

If you really want to burn a disc, here's a tutorial from aysiu: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by ARandomKid on 2007-06-21
Figured since I have nothing to lose, I'd try the update manager. I went and commented out the automatix repositories like you said, but it gives me this after a bit:

> "An error occured during the update. This is usually some sort of network problem, check your network connection and retry.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz) 404 Not Found
"

And then quits. Any ideas?

---

### Post by NeoLithium on 2007-06-21
To upgrade from Dapper to Edgy, just replace (ctrl+h) all instances of 'breezy' with 'dapper' within the etc/apt/sources.list.

Then you can just run:
```

sudo aptitude update 
sudo aptitude dist-upgrade

```

---

### Post by ARandomKid on 2007-06-21
Alright, I've started that and it seems to be going smoothly...thanks for helping me learn something which is probably rather basic...

thanks again!

---

### Post by jfinkels on 2007-06-22
> **NeoLithium said:**
> To upgrade from Dapper to Edgy, just replace (ctrl+h) all instances of 'breezy' with 'dapper' within the etc/apt/sources.list.

Then you can just run:
```

sudo aptitude update 
sudo aptitude dist-upgrade

```

Although this works, it is not the recommended way to perform a distribution upgrade.

---

### Post by ARandomKid on 2007-06-22
^Worked fine for me...

plus, it's really the only way I've found to successfully upgrade from breezy, seeing as I currently can't burn iso files.

Meh. Might not be the recommended way, but it served my purposes.

---

