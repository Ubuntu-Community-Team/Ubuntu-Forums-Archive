---
title: "Zip and RAR Files"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by G!zZm0 on 2008-02-05
I tried to open a .rar file on my Ubuntu and it wouldn't let me. It says:"Could not open file. File is not supported"...Can anyone help me on how to open .zip and .rar files???

---

### Post by solitaire on 2008-02-05
check this thread:
[RAR files]("http://ubuntuforums.org/showthread.php?t=687251&highlight=RAR+files")

---

### Post by jordanmthomas on 2008-02-05
> **G!zZm0 said:**
> I tried to open a .rar file on my Ubuntu and it wouldn't let me. It says:"Could not open file. File is not supported"...Can anyone help me on how to open .zip and .rar files???

Do .zip files also not open or is it just .rar?  Zip files should be openable out of the box.

---

### Post by wolfen69 on 2008-02-05
install ark. it's in synaptic.

---

### Post by FuturePilot on 2008-02-05
File Roller (the default archive manager in Gnome) can open and create .rar files. You just need to install the proper tools
```
sudo apt-get install rar unrar
```

---

### Post by hyperair on 2008-02-05
> **wolfen69 said:**
> install ark. it's in synaptic.

Ark still requires rar and unrar to open/create .rar files if I'm not mistaken.

---

### Post by erginemr on 2008-02-05
I don't recommend installing Ark.

Ark is a KDE program. If you are using Gnome and have not installed any other KDE application such as Amarok, K3b or Krusader, then the installation of ark along with other KDE libraries will take approx. 65 MB. Moreover, running Ark will also have those libraries loaded to the memory, which means extra overhead for a Gnome-only system.

FileRoller, in my opinion, is on par with Ark and is sufficient and will act as a front-end to rar, 7-zip, arj, etc., if you install them from Synaptic.

---

### Post by G!zZm0 on 2008-02-05
I havent tried .zip files, since all the files I've downloaded are .rar type.

---

### Post by Nythain on 2008-02-05
depending on wether or not it got installed during the initial set up, .zip files might require the download and installation of 7zip<?> i believe is the name of the package... rar and unrar are two packages to give you rar support... and there are many archivers out there from
ARK - KDE
FileRoller - Gnome aparently
Xarchiver - Xfce's archiving program, and what i use in fluxbox

---

### Post by Trail on 2008-02-05
Rar format is not supported by default because it is not free as in free-speech. This is the same reason why codecs like mp3 are also not supported by default etc.

Ubuntu sets a clear line on what it supports by default, and that excludes non-free software. If you wish to use such non-free software (marked as restricted), then you can install them manually.

I know it sounds a bit inconvenient at first, but if I wanted to be trapped in closed-source software, I'd be running Windows (well, not really, but whatever). I agree with Ubuntu's policy and I also don't support such formats myself.

Offtopic: Use .iso format on images unless you really have to!

---

### Post by hyperair on 2008-02-05
> **Nythain said:**
> depending on wether or not it got installed during the initial set up, .zip files might require the download and installation of 7zip<?> i believe is the name of the package... rar and unrar are two packages to give you rar support... and there are many archivers out there from
ARK - KDE
FileRoller - Gnome aparently
Xarchiver - Xfce's archiving program, and what i use in fluxbox

7zip is a package to provide support for .7z archives. 7zip archives. They're different from regular .zip files.

---

### Post by andybleaden on 2008-02-05
I have/had  Ark and have used it in Kubuntu for a while and found it really useful in my limited experience

---

### Post by hyperair on 2008-02-05
I believe erginemr had made a point earlier in the thread (post #7) when he said that installing Ark on a GNOME system isn't the best idea to do. In fact, I think the thread has outlived its main purpose which is to let on the method of opening rar files in Ubuntu (GNOME). Perhaps it's high time that this thread was marked solved.

---

### Post by stchman on 2008-02-05
> **G!zZm0 said:**
> I tried to open a .rar file on my Ubuntu and it wouldn't let me. It says:"Could not open file. File is not supported"...Can anyone help me on how to open .zip and .rar files???

You need the rar plugin.

```
sudo apt-get -y install rar unrar p7zip p7zip-full
```

This will install the rar and 7zip packages for File Roller.

---

