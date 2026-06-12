---
title: "Privat Repository"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2007-10-08
I want to create a private repository on my hard disk so that I do not have to download all the files using inter after reinstalling UBUNTU.

Can any one give me a ready tutorial for the job?

---

### Post by julian67 on 2007-10-08
[APTonCD]("http://aptoncd.sourceforge.net/")

> What is APTonCD?

APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of your .deb packages located in one especific repository, so that you can install them into your computers without the need for an internet conection.
With APTonCD you be able to...

Backup
    Backup all downloaded packages (via apt-get, aptitude and synaptic) to restore later.
Transport
    Take with you all your favorite packages, in a removable repository where you can install then all on anytime, anytime.
Download
    Get an entire repository, or a specifc section. Simply point-and-click, and in few time you'll have an CD(s) or DVD(s) with entire main, restricted, universe, multiverse, contrib, etc.
Share
    Share your packages with your friends without Internet conection. Also, send a meta-package for him to install the same set of packages that you have.



---

### Post by capink on 2007-10-09
1. define environment variable $private

```
private=path/to/the/private/repository
```


2. Create the package index file in the private repository:
```

apt-ftparchive packages ${private} > ${private}/Packages
sed  --in-place 's_Filename: '${private}'/_Filename: _' ${private}/Packages
gzip -9c "${private}/Packages" > ${private}/Packages.gz
```

3. Add $private repository to sources.lst

```
gedit /etc/apt/sources.lst
```

and paste the following line into the file:

```
deb file:///path/to/the/private/repository ./
```

**Note:** for this repository to take priority over ubuntu repositories, it must be listed above them in the sources.lst repositories

4. Update apt-get lists

```
sudo apt-get update
```

=====================


If this is too much for you. I attached a script named repo that would do it automatically for you. It is a matter of running the following commnad (after copying the script to /usr/bin and making it excutable):

```
repo --no-sign --dir /path/to/your/private/repository
```

You will also need to add the repository manually to sources.list:

```
sudo gedit /etc/apt/sources.lst
```

And paste the following

```
deb file:///path/to/the/private/repository ./
```

**Note:** for this repository to take priority over ubuntu repositories, it must be listed above them in the sources.lst repositories

The script provide other options like doing multiple repositories, creating release file, signing repositories ... etc

---

### Post by Guruprasad on 2007-10-09
> **julian67 said:**
> [APTonCD]("http://aptoncd.sourceforge.net/")

Thank you.... Julian.

I am looking for repository on hard disk as not all office computers have cd rom.

Guru

---

### Post by Guruprasad on 2007-10-09
> **julian67 said:**
> [APTonCD]("http://aptoncd.sourceforge.net/")

Thank You capink

A perfect reply to my querry.

i was able to manage without the ready script.

I didnt understand what happens with
¨sed  --in-place 's_Filename: '${private}'/_Filename: _' ${private}/Packages¨

Guru

---

### Post by julian67 on 2007-10-09
> **Guruprasad said:**
> Thank you.... Julian.

I am looking for repository on hard disk as not all office computers have cd rom.

Guru
 
CD/DVD drive should not be necessary as .iso files can be mounted in the same way. You could have a single .iso file on server and have all your clients have it mounted read only....but I see you posted while I write this and capink's method is good for you...we have the luxury of choice :)

---

