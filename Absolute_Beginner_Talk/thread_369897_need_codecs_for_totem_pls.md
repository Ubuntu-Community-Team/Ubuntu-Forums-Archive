---
title: "need codecs for totem pls"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-02-25
hello there.. i have been searching for some similary threads for half an hour but nothing seemed to be what i was looking for. i know the last time when i searched for this (totem codecs) i found immediatly but now it seems its gone so, can somebody give me a link or something to install the correct codecs for totem? i wanna play mpg, mpeg, avi files with it :) please help!!! 

thanx in advance.

---

### Post by highneko on 2007-02-25
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Have you tried this link? Good luck, have fun. n_n

---

### Post by r4ik on 2007-02-25
For 5.10

[http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Multimedia_Codecs)

---

### Post by the_nomad on 2007-02-25
yes.. i forgot to specify i have ubuntu 5.10, sorry my bad...

r4ik: i tried that but to all those packages i get the following message
```

Reading package lists... Done
Building dependency tree... Done
Package the_package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package the_package has no installation candidate

```

any ideas? thanx

---

### Post by r4ik on 2007-02-25
Did you add the repo's ?

[http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories)

---

### Post by the_nomad on 2007-02-25
yes i have tried and i have followed the instructions exactly how they are at that link you gave me but i got this error

```

http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
```

followed by a warning that says:

```

The following problems were found on your system:

W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)

```

---

### Post by r4ik on 2007-02-25
If you're internet allows it consider an upgrade,

[http://ubuntuguide.org/wiki/Ubuntu#How_to_upgrade_from_Breezy_Badger_to_Dapper_Drake_.28experimental.29](http://ubuntuguide.org/wiki/Ubuntu#How_to_upgrade_from_Breezy_Badger_to_Dapper_Drake_.28experimental.29)

and try,

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

And you will be more up to date.
I am not even sure those 5.10 repo's still work.

---

