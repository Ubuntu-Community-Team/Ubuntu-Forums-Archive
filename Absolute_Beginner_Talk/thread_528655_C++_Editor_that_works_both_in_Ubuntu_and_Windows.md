---
title: "C++ Editor that works both in Ubuntu and Windows"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by tisse on 2007-08-18
Hi,

I'm looking for an Editor that works both in Ubuntu and Windows because I use ubuntu at home and windows at work. I will mostly use it to code C++ and a bit of Perl and Python. Thanks in advance.

---

### Post by Zalbor on 2007-08-18
I think Scite has a windows version.
But may I ask, why is it so important that it's the same editor? As long as you save the code in a simple text file, any editor should be able to open it. The only problem might be the CR/LF issue, but even some windows editors get around it and it's easy to convert a file.

---

### Post by cmnorton on 2007-08-18
I use Epsilon for all development on Linux and Windows, including writing procedural notes, when I want those to be strictly text without formatting. Epsilon's web site is [www.lugaru.com](www.lugaru.com). Their support is excellent.  

I don't know if GNU emacs customizations could be preserved across platforms. My guess is they could be, if you want open source.

There is SlickEdit, but you pay for each license, Windows and Linux. With Epsilon, you pay for one license that you can install on both Epsilon and Windows, as long as you are the user on both platforms.

---

### Post by luisromangz on 2007-08-18
You can try the C/C++ plugin for Eclipse.

---

### Post by Mr.Carramba on 2007-08-18
> **luisromangz said:**
> You can try the C/C++ plugin for Eclipse.

actually you can run it as C/C++ ide [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/) not just plugin
thing to take in account is that cygwin/myngwin are behind  in version of  compilers.
I'm not sure but I think they are still using gcc 3.x port.
anyway you can install very nice non-official port: [http://www.develer.com/oss/GccWinBinaries](http://www.develer.com/oss/GccWinBinaries) for the moment running gcc 4.1.2 if you don't need *nix environment .
and remember to exclude preferences from cvs commit, because of different path's between systems.

---

### Post by vexorian on 2007-08-18
[Code::blocks](http://www.codeblocks.org/) , nuff said.

---

### Post by tisse on 2007-08-19
Thanks for the suggestions. I agree with you that I don't really need the same when in Ubuntu and Windows, its better to use the best in windows and the best in Ubuntu. For windows I will probably use notepad++ (because it's popular at work), and for Ubuntu I will read through your suggestions, thanks!

---

### Post by Max Luebbe on 2007-08-19
> I agree with you that I don't really need the same when in Ubuntu and Windows, its better to use the best in windows and the best in Ubuntu ..except when they're the same!

Use Emacs!:guitar:

---

### Post by rharriso on 2007-08-19
I know there are a couple of C++ IDE that come with the KDE programming set, those work fairly well, but I use the gui text editors such as Kate or Gedit and compile with the command line. I find that to be much easier. 

For windows if youre looking for an IDE C-Free and Bloodshed are some pretty good ones as long as your are command line compiling. Compiling with the IDE can be a bit of a pain.

---

### Post by vexorian on 2007-08-19
> **tisse said:**
> Thanks for the suggestions. I agree with you that I don't really need the same when in Ubuntu and Windows, its better to use the best in windows and the best in Ubuntu. For windows I will probably use notepad++ (because it's popular at work), and for Ubuntu I will read through your suggestions, thanks!
my ultra biassed point of view is that code::blocks is the best alternative in both environments :)

---

