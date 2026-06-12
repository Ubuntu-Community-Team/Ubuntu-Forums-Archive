---
title: "How do I know what a package does?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by kentl on 2007-08-29
Hi!

I know how to install, update and remove packages using Apt or Aptitude, of which I nowdays prefer the latter. Apart from that I do not know the package system well, or even Linux, but I'm trying to learn while doing. :)

My most recent issue is when [installing DenyHosts for my home server]("http://ubuntuforums.org/showthread.php?p=3273397#post3273397"). It works and it got installed as a daemon (even though I would have preferred to run it as a cron job, it still works so I am fairly happy).

How do I know what a package does to my system? I know how to find them, install them and remove them. But what about what actually happens?

After reading the man page for Aptitude I tried:
```

kent@cow:~$ aptitude -v show denyhosts
Package: denyhosts
State: installed
Automatically installed: no
Version: 2.6-1
Priority: optional
Section: universe/net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 422k
Architecture: all
Compressed Size: 62.4k
Filename: pool/universe/d/denyhosts/denyhosts_2.6-1_all.deb
MD5sum: a78e0eafb78bcb1b27d1afc8d8809b1c
Archive: feisty, now
Depends: lsb-base (>= 3.1-10), python, python-central (>= 0.5.8)
Conflicts: denyhosts-common, denyhosts-python2.3, denyhosts-python2.4
Replaces: denyhosts-common, denyhosts-python2.3, denyhosts-python2.4
Description: an utility to help sys admins thwart ssh hackers
 DenyHosts is a python program that automatically blocks ssh brute-force attacks
 by adding entries to /etc/hosts.deny. It will also inform Linux administrators
 about offending hosts, attacked users and suspicious logins.

 Syncronization with a central server is possible too.

 Differently from other software that do same work, denyhosts doesn't need
 support for packet filtering or any other kind of firewall in your kernel

```
But it didn't really give me what I want.

Ideally I would like to know before I install the package what it will do to my system. But if that's not possible knowing what it actually did would be nice? When installing the above program it added a daemon to my startup processes. And to be honest I don't know where the actual script is located. :-)

Hope you can give me some information. I've tried to look around the Ubuntu Guide and wiki but didn't really get what I wanted. 

I hope someone can help me. Knowing what actually happens during package installation would probably be a good learning experience for me who have pretty shallow Linux knowledge. Thanks for reading!

---

### Post by bapoumba on 2007-08-29
For packages with no infos on the wiki, I usually google it and try to find a home page, or a sourceforge page.
[http://denyhosts.sourceforge.net/]("http://denyhosts.sourceforge.net/")
[http://sourceforge.net/projects/denyhosts/]("http://sourceforge.net/projects/denyhosts/")

There are usually contact links, sometimes forums, FAQ or wikis, install procedures and such.
[http://www.ubuntugeek.com/securing-ssh.html]("http://www.ubuntugeek.com/securing-ssh.html")

---

### Post by kentl on 2007-08-29
What I have done:
[LIST]
[*] Found its homepage and read everything on it, including the FAQ
[*] Read everything on the external sites linked to from the homepage under the subheader "As seen elsewhere"
[*] Read the man page after installation of the package
[*] Carefully examined the config file for information
[*] Done "aptitude -v show denyhosts" and read it all
[/LIST]

Correct me if I'm wrong, but a script like this is usually added to the Debian repository by someone other than the original author (OA). As the OA can't be bothered to add it to every repository of each Linux distribution. This other person who add it to the repository decides on what the installation package will do, like install it as a daemon automatically.

Contacting the OA wouldn't help me. And how do I get hold of the package creator? And is this the proper way, to e-mail the package creator and ask him/her what it actually does before you install it? Isn't there another way to see what it does? Like if it installs daemons, which config files it adds/changes and where it puts its files?

If the mail approach is the only way. I think I see a possible improvement to this whole way of installing things. :KS

---

### Post by rsambuca on 2007-08-29
Why not go through the source code to see what it does?

---

### Post by bapoumba on 2007-08-29
[http://changelogs.ubuntu.com/changelogs/pool/universe/d/denyhosts/denyhosts_2.6-1/changelog]("http://changelogs.ubuntu.com/changelogs/pool/universe/d/denyhosts/denyhosts_2.6-1/changelog")
[http://changelogs.ubuntu.com/changelogs/pool/universe/d/denyhosts/denyhosts_2.6-1/denyhosts.copyright]("http://changelogs.ubuntu.com/changelogs/pool/universe/d/denyhosts/denyhosts_2.6-1/denyhosts.copyright")
May be the dev who packaged it? Or the [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss") mailing list ?

---

### Post by nbkr on 2007-08-29
If I don't know what a package will do I download .deb file and do a dpkg -c package to show what files the package will install. 

After that I unpack a package and have a look at the pre-install scripts that the package will run. So I'm able to see what the package will do or change on my system when I'm going to install it.

---

### Post by kentl on 2007-08-29
> Why not go through the source code to see what it does?
Do you mean the source code of the install package? If no, I haven't made it clear what I want to do. I want to know what the installation of the package will do to my system, not how the installed application works.
> [http://changelogs.ubuntu.com/changel....6-1/changelog](http://changelogs.ubuntu.com/changel....6-1/changelog)
[http://changelogs.ubuntu.com/changel...osts.copyright](http://changelogs.ubuntu.com/changel...osts.copyright)
May be the dev who packaged it? Or the ubuntu-devel-discuss mailing list ?

Thanks! That defenitely is interesting information. Through the changelog I won't know what it does to my system during installation. Perhaps the information is "hidden" in there, but there are a lot of information in the log. In fact, so much, that I find it very hard to know what it does. It must be a good place to learn about updates to packages that you have good knowledge of already.

The second link shows me that the "package was debianized by Marco Bertorello" and gives me his e-mail address. But this solution involves contacting the debianizer(?) for each package I want to learn about before installing it. And if the debianizer haven't got time to answer it's a dead end.

Asking on the mailing list seems like a better alternative. But only slightly. It's probably only the debianizer in question or maybe someone else too who can answer. And then we have the same situation as with an e-mail.
> If I don't know what a package will do I download .deb file and do a dpkg -c package to show what files the package will install.

After that I unpack a package and have a look at the pre-install scripts that the package will run. So I'm able to see what the package will do or change on my system when I'm going to install it.
This is what I was looking for. It seems like a lot of trouble but if it's the only way then that's the way I'll have to go.

Do you have any good method to find a .deb file for a package? And how to download it? And how to extract it?

---

### Post by rsambuca on 2007-08-29
If you are really concerned about how it will be installed, why don't you go from the source code, and do the old ./configure command.  This will then create a Make file which you can go through to see how it will be compiled and installed on your system.

---

### Post by kentl on 2007-08-29
In that case, won't I have to update it manually from that point on? I want to have full control, or at least full visibility, without sacrificing the useful ability to update things in a smooth manner.

I think that there is room for something in between "knowing all, but getting no automation in maintenance" and "knowing very little, but getting full automation in maintenance". I know I want something in between.

I'll look into nbkr's suggestion, as it from my view, seems like the best approach. If I'm lucky I'll find looking at pre-install scripts from a decompressed .deb-file about as difficult as looking at a Make-script. But as I've only seen the latter I don't know.

---

### Post by capink on 2007-08-29
If I understand what you want correctly, here is how to do it:

1. Install apt-file

```
sudo apt-get install apt-file
```

2. Update apt-file lists

```
sudo apt-file update
```

Note: This will take sometime depending on the speed of your internet connection.

3. To know what files a certain package would install on your system:

```
apt-file list packagename
```

It goes without saying that this will only work for packages in the repositories.

---

### Post by rsambuca on 2007-08-29
How about if you just use Synaptic for a package you have installed.  Right-click the package, and select "Properties".  In there you will find a tab that says "Installed Files".  It shows where everything got put.  Obviously a in hindsight type of thing, but at least you know where everything got put, as you say!

---

### Post by kentl on 2007-10-28
A long overdue answer, but I'd still like to thank you all. I use apt-file now and it fulfills my need. You're able to know where a file will get put for packages you haven't installed as well. So it couldn't be much better (it could be a little better, if I knew which changes would be made to my system as well [changed config files and new user accounts etc]).

---

