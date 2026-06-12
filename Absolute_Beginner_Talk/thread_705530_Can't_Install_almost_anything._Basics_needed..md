---
title: "Can't Install almost anything. Basics needed."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by penguinv on 2008-02-23
Hello Fellow Users,

I cant seem to install anything that does not install itself.
Eg of things that install themselves: flash in Firefox, LostIRC, Opera.
They are "Well Behaved" and how I expect a GUIsystem to be.

Eg of things I cant install: flash in Opera, anther IRC client (forget which now), azurus, kbittorrent, deluge.

Eg of something I strugged with, finally installed and forgot how (almost): Java [The crux was, in a terminal window, to chose Yes, the only one choice, I had to push an arrow key, normally used to move _between_ choices, to highlight the choice so that the <enter> key could choose it. Now the fault there was clearly with the Java Folks who did not want to leave a chance of a No answer.- and yet, they set it up so that I had to act as-if the No answer was there. Baffles me.]

OK now let me settle down and talk about deluge, my latest attecpt to install a bittorrent client. We have words like
download, archive, package manager, dependencies.
I have figured out that synaptic, apt-get, etc are frontends for some other package manager that is prolly run in a terminal shell. Maybe I should just learn to use that one. (Learned this in [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/))

(dependent para) quoting
This system is called the package manager and on Ubuntu you'll meet it in the form of apt-get, aptitude, Add/Remove..., Update Manager and Synaptic. All these programs are frontends to the same package manager[2] built right into Ubuntu.
(2) Advanced Packaging Tool or APT is what empowers many popular Linux distributions. It was first seen in Debian (that's where the name of the packaging format, deb, came from) but is now also used by other popular distributions such as Ubuntu, Knoppix, Linspire and Mepis. Another popular package manager is RPM (RPM Package manager, a recursive acronym) which is used by Fedora Core, SUSE Linux and Mandriva.

But nothing tells what it is. How it works. What a package is.

Is a package the archive I haev a choice of? What is extracted from the archive?

I started Symantic. I saw a long list of strange names. Are these packages? Are they already on my hard drive? If so what's the point of saying -- but just that Windows programs typically include parts of libraries in their installers, taking up lots of space after they've been installed because the same libraries have duplicates many places on your harddisk; Linux programs usually don't do this. -- if Linux puts all these things on my hard drive.

And in another place it suggests that Synaptic must look on the net in repositories for "packages" If so, then why do all these pages have download sites for programs, and not tell me to go start Synaptic first.

Guys, when I understand this I am going to write a beginners guide that doesn't stop people from using the system. This is like a highschool clique. Except the rhetoric READ THIS CANONICAL is that it's for everyone.

Does Synaptic access the web? Have I been looking in repositiories? Are repositories something else? Debian looks easy or does it, oh then it says it only works if you already know how to install something or other and have installed it. Jolly well circular.

Its a cruel game you play and I want to open the field.
Ay masters, we slaves shall be freed.


[INDENT]One more try, I started synaptic. I did not see any way to get on the web or search there. I searched for deluge, already downloaded. Nada. Story to be continued.[/INDENT]

---

### Post by forestpixie on 2008-02-23
If you've actually got a question ask it.

---

### Post by penguinv on 2008-02-23
I found these:

Apt repositories are currently available for Ubuntu systems running Ubuntu Dapper or later on either i386 or amd64 systems. To add the repository, add one of the following lines to your /etc/apt/sources.list (replace VI with GEDIT or alike text editor):

apt-get.org is intended as a place for people to share useful APT (Advanced Package Tool) sources for the Debian operating system.

What are Repositories?
There are thousands of programs available to install on Ubuntu. These programs are stored in software archives (repositories) and are available for installation over the Internet. This makes it very easy to install new programs. It is also very secure, because each program you install is thoroughly tested and built specifically for Ubuntu.
The Ubuntu software repository is organized into four "components", on the basis of the level of support Ubuntu can offer them,

Adding Repositories in Ubuntu (a title)  -- adding repositories to what? how?
 The operations described on this page modify the software repositories configuration file located at    *      /etc/apt/sources.list 
-- ok thats something on my computer. This is a list of some kind.

Adding the Universe and Multiverse Repositories
    *      Navigate to "System" > "Administration" > "Software Properties".

-- yes and my system dialog boxes are different than what it shows. And besides I already have everything checked.

Back to being nowhere.. 
Till later.

---

### Post by aroch1 on 2008-02-23
> Ay masters, we slaves shall be freed.

Package management's always holdin' you down! Arise and fight! lol....there is no clique

Some programs are packaged for Ubuntu and are in the repositories that you see in Synaptic.  Some aren't or have released newer versions that aren't in the repositories that you can download and install from their websites.

Synaptic accesses the web.  The packages you see listed line by line are in repositories maintained online by Canonical.  To install deluge, either fire up Synaptic, click search, enter deluge and search for it.  It should come up with a package called deluge-torrent.  Click the check box on that line and then the apply button on the toolbar, and deluge should download and install.

To use the command line its a little easier...fire up the terminal (Accessories->Terminal)
and enter
```
sudo aptitude install deluge-torrent
```

If you have any more questions, ask them and I'll answer, just drop the rant, its hard to pick out what you want to know from what you're complaining about.

---

### Post by penguinv on 2008-02-25
Re: Can't Install almost anything. Basics needed.  Re: Can't Install almost anything. Basics needed.
> : penguinv
Ay masters, we slaves shall be freed.
Package management's always holdin' you down! Arise and fight!

 lol....there is no clique

> Anoch1: Some programs are packaged for Ubuntu and are in the repositories that you see in Synaptic. Some aren't or have released newer versions that aren't in the repositories that you can download and install from their websites.

Synaptic accesses the web. The packages you see listed line by line are in repositories maintained online by Canonical. To install deluge, either  (do it gui or terminal)
fire up Synaptic, 
[LIST]
[*]click search, 
[*]enter deluge and 
[*]search for it. It should 
[*]come up with a package called deluge-torrent.
[/LIST]
      **Did it, but it is just called deluge, not deluge-torrent**
Click the check box on that line and 
     **I do that and the word deluge is orange, ie selected**
then the apply button on the toolbar, and 
    **but, THE APPLY BUTTON DOES NOT GET ACTIVE**
deluge should download and install.

**FYI, i've already downloaded deluge, as**
/home/computername/deluge torrent download/deluge-torrent_0.5.7.1-1_i386.feisty.deb
AND EXTRACTED IT
/home/dahlia/deluge-0.5.4.1
**Will that help? Does that change things?**


> To use the command line its a little easier...fire up the terminal (Accessories->Terminal)
and enter
Code:             sudo aptitude install deluge-torrent

(Since I dont know quite what this does I want to be careful and learn more first. Sorry.)

> If you have any more questions, ask them and I'll answer, just drop the rant, its hard to pick out what you want to know from what you're complaining about.

NP. I actually ran these things more than once before I added the rant. "Squeaky Wheel" and all that. Apologies.

---

### Post by mali2297 on 2008-02-25
> **penguinv said:**
> 
**FYI, i've already downloaded deluge, as**
/home/computername/deluge torrent download/deluge-torrent_0.5.7.1-1_i386.feisty.deb
AND EXTRACTED IT
/home/dahlia/deluge-0.5.4.1
**Will that help? Does that change things?**

Double-click the .deb file and it should open in the package installer Gdebi. You will find an option to install the package.

---

### Post by PeterJS on 2008-02-25
Software in linux is handled by a package management system, which is made up of three big parts on the local machine: the list of where the repositories are, and a local master list of what is in every known repository, and  the list of what is currently installed.

The list of known repositories is in /etc/apt/sources.list, and contains a listing of repositories including what type they are (deb or deb-src), where they are (usually in the form of an http url), which version of ubuntu they are for, and which sections they include. Canonical breaks everything they provide in to 5 categories: Main, Restricted, Universe, Multiverse, and partner. Other repositories may provide other sections, the name of which usually describes it's contents or license.
Main and Restricted are officially supported by Canonical, and in theory contain everything a desktop needs (this doesn't hold in practice). Universe and Multiverse are community maintained and not officially supported. Main and Universe are completely legally in the clear, anything in them can be installed and used in any way allowed under the GPL, no questions asked. Restricted and Multiverse are on less solid ground and generally contain things that have licensing requirements that make them non-free. And partner is stuff that is whole sale commercial, Opera, VMware, etc.

APT keeps a local listing all of the packages it knows about and their metadata (size, location, dependencies, etc), so when you ask it to install something the first thing it does is check the list of things it knows about, if it doesn't find it, it returns and error and stops right there. If it does find it the next step is to check that all of the dependencies have been installed, if they have it will then pull the package from it's known location (in the repository) and install it. If the dependencies aren't installed it will attempt to install them using the same process as with the original request.

The last local component is the list of installed packages, and which files they include. This serves two main purposes, the dependency check mentioned above, and uninstalling things. Since each package has  precise list of which files it owns uninstalling package is quite easy, apt just deletes all the files for that package and removes it from the list of installed packages.




A repository is made up of two big components, it's listings and it's content. The listings are a group of cryptographically signed and compressed lists of which files the repository has and what version they are. This allows them to be downloaded, verified as legitimate, and then integrated in to the local package index. The packages themselves make up the bulk of a repository and are packaged in the Deb package format.

The deb package format is an archived file that is made of two sub archives, the first one describes what contents of the second one. The first archive is the control archive and contains the version of the deb standard the file uses, what files are in the payload archive, which package the file is, what version it contains, and a copy of it's dependency list. When a deb package is installed the first archive is unpacked and has all of it's information recorded in the relevant locations, once that is done the second half is extracted to it's proper location in the file hierarchy (see the link in my sig, if you want to learn more about the file layout).

As for installing stand alone deb packages you're best option is to double click on them which should open them in the Gdebi package installer which will walk you through the rest of the install process.

---

### Post by bodhi.zazen on 2008-02-25
These links help also :

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

	[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

