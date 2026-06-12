---
title: "Repository?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-05-04
I've installed several programs using the add applications routine in Ubuntu, but what I don't quite understand is the this whole "repository."

When you go to use the repository, you are leaving the Ubuntu servers for programs and collecting them off the web from various servers?  

And how exactly do you enable the repository? Not sure If I've done this correctly.

One more question...I'm running Breezy Badger.  When the next release comes along, do I have to do an entire re-install from disk or does Ubuntu update itself somehow?

---

### Post by Qrk on 2006-05-04
The repositories are collections of .debs packages. Apt-get knows which debs depend on what, and where they can be found, this is what apt-get update does. 

The offical repositories are hosted by Ubuntu (archive.ubuntu.com) 

You can enable a repository by adding it's line to /etc/apt/sources.list. For ubuntu repositories, System->Administration->Software Properties works. You can also use synaptic to enable them. 

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Dapper will be the first Ubuntu release to automatically update from the GUI.

---

### Post by georgetoon on 2006-05-04
[QUOTE=Qrk]

Dapper will be the first Ubuntu release to automatically update from the GUI.[/QUOTE]

Thanks for all the great info.:):)

C'mon, Dapper!:):)  Really looking forward to it.:)   Really enjoying Breezy Badger! When is Dapper due for release?

---

### Post by mips on 2006-05-04
Another way to do it, [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by mostwanted on 2006-05-04
[QUOTE=georgetoon]Thanks for all the great info.:):)

C'mon, Dapper!:):)  Really looking forward to it.:)   Really enjoying Breezy Badger! When is Dapper due for release?[/QUOTE]

On June 1st this year ;)

Well, technically it's already been "released" since I'm using it right now, but that's the official release date anyhow.

You might want to check out the link in my sig if you want a more thorough explanation of the whole install/repositories concept.

---

### Post by georgetoon on 2006-05-04
[QUOTE=mostwanted]On June 1st this year ;)

Well, technically it's already been "released" since I'm using it right now, but that's the official release date anyhow.

You might want to check out the link in my sig if you want a more thorough explanation of the whole install/repositories concept.[/QUOTE]

June 1st.:)  Wonderful.:)  So I'll need to download the Dapper .iso, burn to disk and reinstall once more?  If so, I'm hoping all my settings will be remembered.  If not, not a big deal.:)  I'm enjoying the learning experience.:)

---

### Post by mostwanted on 2006-05-04
[QUOTE=georgetoon]June 1st.:)  Wonderful.:)  So I'll need to download the Dapper .iso, burn to disk and reinstall once more?  If so, I'm hoping all my settings will be remembered.  If not, not a big deal.:)  I'm enjoying the learning experience.:)[/QUOTE]

No, you don't have to redownload it, you can upgrade with APT like a regular auto update

```

#This upgrades your system to Dapper Drake
sudo update-manager -d
```

but personally I prefer doing a fresh install with each new release.

---

### Post by georgetoon on 2006-05-04
[QUOTE=mostwanted]No, you don't have to redownload it, you can upgrade with APT like a regular auto update

```

#This upgrades your system to Dapper Drake
sudo update-manager -d
```

but personally I prefer doing a fresh install with each new release.[/QUOTE]

Outstanding!:)  Thank you!:)

---

### Post by confused57 on 2006-05-04
I'm also thinking of upgrading Breezy to Dapper when the final version is released and have seen a couple of ways to do so.  I was wondering which one may be the most reliable:

1.)  gksudo "update-manager -d"   ,  which I guess does it automatically for you.

or  

2.)  Change the sources list repositories from breezy to dapper , then:

     sudo apt-get update
     sudo apt-get dist-upgrade

I realize neither is guaranteed to work, but I'm not sure which would be the best way to go.

Thanks Qrk, that answered my question.

---

### Post by Qrk on 2006-05-04
They will probably be equivalent. gksudo update-manager -d will replace the breezy sources.list with one for dapper.

---

