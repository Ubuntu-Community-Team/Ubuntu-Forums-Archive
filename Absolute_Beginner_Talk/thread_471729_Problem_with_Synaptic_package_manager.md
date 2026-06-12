---
title: "Problem with Synaptic package manager"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by adil_mughal on 2007-06-12
Hello everyone,

I seem to have recently developed a problem with my synaptic package manager. When ever I try to install anything using synaptic package manager, marking a package for installation yeilds a window saying 

WARNING

you are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system

if I then proceede with the installation any way I get error messages which typically look like:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_6.3-078+1ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_6.3-078+1ubuntu3_i386.deb)
  404 Not Found

Any one know what I am doing wrong.

Many, many thanks in advance

---

### Post by kevinmedina on 2007-06-12
Are you on-line when trying to install this package?  Did you experience this problem with any other deb packages?

---

### Post by Cypher on 2007-06-12
If you click on the link you provided, you will notice that you will get a 404 error. So APT is reporting that. Looks like the version of the file you are requesting doesn't exist. Within Synaptic ask it to reload/update it's info..

---

### Post by adil_mughal on 2007-06-12
Thank you for your replys.

I should be online (launching a browser is fine and I can navigate the web fine). Furthermore I am experencing this problem with many different packages.

However, clicking on the reload button yeilds a number of error messages which start with:


-----------------------------------------------------------------------------------------------------------------------

Could not download all repository indexes

the repository may no longer be available or contacted due to nework problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writting of the repository addresses in your preferences.

[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:) 404 Not Found
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:) 404 Not Found

---------------------------------------------------------------------------------------------------------------------------------

so perhaps there is an error with  writting of the repository addresses? If so do I need to make some sort of modification under 

settings -> preferences

or 

settings -> repositiories

I don't recal fiddling with either of these in the recent past!

Adil

---

### Post by Najand on 2007-06-12
open a terminal and type:
```

sudo apt-get update

```
Do you get the same error?

---

### Post by Cypher on 2007-06-12
The issue is simple..you are using Breezy Badger. You are pointing to gb.archive.ubuntu.com as your repositroy, but that respository no longer houses the Breezy code.

You may want to update your Linux to Edgy or Feisty..

---

### Post by adil_mughal on 2007-06-12
Yes I get some error messages containing 404 Not Found, here is the full print out

Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  404 Not Found
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  404 Not Found
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  404 Not Found
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  404 Not Found
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Sources
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Cypher on 2007-06-12
Read my [reply]("http://ubuntuforums.org/showpost.php?p=2829647&postcount=6")..:)

---

### Post by adil_mughal on 2007-06-12
How do I update my package to Edgy or Feisty? I am sure this is something that must be staight forward for experenced users, is it something I can do using synaptic package manager? Can you point me in the right direction with regards to instructions? Clearly this makes me a little bit wary as I don't want to damage any of my existing ubuntu set up.

Yours

Adil

---

### Post by Cypher on 2007-06-12
What you are experiecing right now is basically Ubuntu stopping support for Breezy Badger as Dapper Drake, Edgy Eft and Feisty Fawn are the currently supported distributions. Even if you don't want to jump all the way to the latest version (Feisty Fawn), you should upgrade to Dapper Drake or Edgy Eft at least..

Yes, the Synaptic Package Manager can handle the upgrade for you, but you will need to point it to the new Dapper/Edgy/Feisty sources. So do the following in a terminal
```

gksu gedit /etc/apt/sources.list

```
Go through and replace any references to Breezy with Dapper. Save the file. Then load up the Update Manager from System->Administration->Update Manager and go through the update to Dapper. 

If all works and nothing horribly breaks, you can tempt fate with an update to Edgy Eft and then Feisty Fawn..

---

### Post by adil_mughal on 2007-06-12
ok so using the command

gksu gedit /etc/apt/sources.list

brings up a file. I then use gedit's search and replace function to replace all occurances of the word "Breezy" with "Dapper".

Then I open the the update manager:

At this point do I click on "install upgrade" or on the button saying

New distribution release is available... upgrage

(clicking on install upgrade leads to error messages printed below.

Sorry for being so slow with all this stuff and thanks to you for taking the time to help me out...


--------------------------------------------------------

W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) Dapper-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_Dapper-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) Dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Dapper-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) Dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Dapper-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) Dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Dapper-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) Dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Dapper-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by adil_mughal on 2007-06-12
Furthermore upon hitting the upgrade button I got the following errors

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/Dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/Dapper-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/Dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/Dapper-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/Dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/Dapper-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/Dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/Dapper-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/Dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/Dapper-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/Dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/Dapper-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/Dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/Dapper-security/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/Dapper-backports/multiverse/source/Sources.gz) 404 Not Found


yours

adil

---

### Post by Seisen on 2007-06-12
Change "Dapper to "dapper" then try it.

---

### Post by adil_mughal on 2007-06-12
ok that seems to have started things rolling, Thank you.

I will send another post when the system has finished up dating. In the mean time thatk you, thank you very much you wonderfull people!!!

---

### Post by Seisen on 2007-06-12
Good deal, I tried the link with "Dapper" in it and it wouldn't work so I changed it to "dapper" and it worked. Sometimes the solution is right in front of you staring at you.

---

### Post by adil_mughal on 2007-06-12
Everything is working great now. Wow Thanks guys!!!!!

---

### Post by Cypher on 2007-06-12
That's great to hear. But know that you just updated from an unsupported version to the last supported version. There is still Edgy Eft and Feisty Fawn ahead of Dapper Drake. And you might face this issue again if you don't take the opportuntiy to upgrade to the newer versions at some point..

---

