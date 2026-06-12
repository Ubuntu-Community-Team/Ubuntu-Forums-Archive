---
title: "Installing Software Downloaded (Example: Divx Decoder)"
date: 2005-05-31
forum: Absolute Beginner Talk
---

### Post by j0sh3rs on 2005-05-31
I'm still a major rookie to Linux, and I just need some reference to how to install some freshly downloaded software.  I know there's a console command, just wondering what it is.  My example is that I'm trying to install the divx decoder from Divx's website, and, unlike windows, I can't just double click on the shell install script that came out of the tar.gz file.

Thanks for putting up with the dumb question(s) I've got.

~Josh

---

### Post by cinematography on 2005-06-01
Linux installs programs differently than Windows. For most cases you can just go to your package manager and download what you want. That can be found under System -> Administration. Or you can use this nifty little command called apt-get. To install gnomebaker (CD burning program) for example, you can type in 'sudo apt-get install gnomebaker'.

To install a .deb file that you've downloaded, you enter this command:
sudo dpkg -i TheNameOfTheFile.deb

That is if there is a .deb file inside of that tar.gz. If not, there may be a simple shell that you can click on like you did when you were using Windows.

---

### Post by zenlord on 2005-06-01
[QUOTE=j0sh3rs]My example is that I'm trying to install the divx decoder from Divx's website, and, unlike windows, I can't just double click on the shell install script that came out of the tar.gz file.[/QUOTE]
You are far easier off using Synaptic Package manager or apt-get to install the mpg123-package. This package contains everything you need to decode divx and xvid.

Installing software from a site (without apt-get or synaptic) is not recommended because of the missing optimisations. And on top of that, if a package is updated, you will not be notified by Gnome/Ubuntu.

You might need to add universe/multiverse to your resource list to be able to select mpg123, so if you haven't done that already, please search this forum or take a look at the ubuntuguide.org

Zl.

---

