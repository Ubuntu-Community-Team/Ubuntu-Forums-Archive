---
title: "Absolute beginner tring to install Open Office 2.1 needs help"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Roger_Melly on 2007-03-05
Hello,
So far I have found a deb package that I have downloaded to my desktop and it is sitting there  as a tar.gz

I have tried to read through some other threads but they make no sense to me.  
Can someone please help me through this bit?

Cheers

---

### Post by hyper_ch on 2007-03-05
why don't you use the OOo provided by the repository? It may not be the most current version but using software from the repos is mostly the best option...

However if you want to go ahead, you first have to extract the deb file from the archive. Right click on it and you should be presented an option to "extract here"... once that is done and if there's a deb then, you can doubleclick that one.

---

### Post by Roger_Melly on 2007-03-05
hyper_ch,
the bundled version 2.04 has several java problems and I can't use the BASE wizards.
When I double click a pack I'm told there are dependency issues.

---

### Post by JermainWijnhard on 2007-03-05
open adapt manager, and search in the repositories for open office. If you install it from there, your computer will automatically download and install all required dependencies.

---

### Post by hyper_ch on 2007-03-05
Roger

did you install the proper java?
Maybe that would help

Execute from the terminal
```

sudo apt-get update

```
then
```

sudo aptitude install sun-java5-jre

```

and get OOo installed:
```

sudo aptitude install openoffice.org

```

If that does not help, then you will have to see what dependencies 2.1 requires and install them first.

---

### Post by Roger_Melly on 2007-03-05
I think I may have managed guys.  

For those New to Ubuntu like myself sometimes the installation of things seems a little weird at times but this is what I did.

First you are advised to take off all of the old Open Office Software by using the Synaptic package Manager.  Search for "Open Office" and mark all the entries with green boxes.

You then need to download the new version without the faults.
I found a link to a debs version of Open Office v 2.1 [URL="http://www.ubuntuforums.org/showthread.php?t=316934&page=5"][COLOR="Sienna"]here[/COLOR]
[/URL]  see Lewmniks entry.

I went there and found the OOo_2.1.0_LinuxIntel_install_en-US_deb.tar.gz

I downloaded this by double clicking which opened the Archive manager.  I left the default settings and downloaded the file.

Eventually it sits on your desktop as a STILL UNPACKAGED directory (this is what I used to call a file)  You cannot open a terminal and cd to this unpackaged directory you must unpackage it first!

Double click the unpackaged icon on the desktop and when the Archive Manager opens go to the top left corner where it says "Archive" and select "Extract".  I then left the default options and away it went.  You should now have two Open Office related packages the tar.gz and a new directory called DEBS.

Open a terminal and cd (goto) this place by typing: cd Desktop/DEBS

This essentially gets you into the folder/directory that you have just created.

Now for what I hope is the last bit.

type: sudo dpkg -i *.deb 

and away it goes.  When it has finished close the terminal and go to applications where you will see your new Office applications.:) 

I would like to thank everyone on the post I linked to it was just a bit confusing for a complete and total numbskull like myself.  Hope it helps someone.

P.S.  I'm hoping to just drag the unwanted folders to my downloads file off my desktop..  I don't know if this will cause any issues

---

### Post by hyper_ch on 2007-03-05
it won't cause issues as you did install the .deb file... it's the same behaviour with windows .exe or .msi files... the installation files aren't needed anymore after the install as the essential files have been extracted to their proper location.

---

### Post by Roger_Melly on 2007-03-05
jermaine 

Thanks for trying to help me.....Sadly this is a problem I am experiencing using these forums where everyone has different names for things.  Is adapt manager "Synaptic package manager" ?  If so I have allowed all directories and can only see the old version.  I think this has something to do with Ubuntus policies as you have to register the newer version???

Hyper_ch

Thanks for the java advice.  I had tried various java solutions but it seems to be a known bug of that version.  It may have even been a security flaw.  I have tried the new version and the buttons "work out of the box" (straight away)\\:D/

---

### Post by hyper_ch on 2007-03-05
Well, regarding adept/synaptic

Those are different packet managers... I don't know which one is installed by default on what system (Ubuntu/Kubuntu/Xubuntu)... I think Synaptic is on ubuntu and xubuntu and adept on kubuntu... but could be vice-versa :)

I normally use the command line to install things... and there you have the option between
apt-get  (install app) and aptidude (install app).
The main difference between apt-get and aptitude is that that aptitude will also install the recommended packages in addition to the required ones...

---

