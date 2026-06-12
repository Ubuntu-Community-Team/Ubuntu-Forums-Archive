---
title: "How do I change system colo(u)rs anf font"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by jaseywasey on 2005-12-07
Hello,
I'm fairly new to linux (although I do have some unix skills). I'm happy to say that I managed to install firefox 1.5, apache, php, mysql. 

Anyway, My eyes aren't great (cateracts removal, glaucoma, uveitus, retinitis, blah blah blah). I'm looking to change some of the colours, specifically to alter ubuntu so that wherever possible white text appears on a black background. I've changed firefox and the terminal.  How can I change the system colours so that the dialogue boxes, that come up, are black with white text. White backgrounds are almost impossible for me to see (took me 4 attempts to register here because of the string verification which is white background and low contrast). 
I've googled about and found a few items but I'm not really sure what I'm looking for. Keywords that come up are gnome, nautilus "system color". I think I've got to create a .gnome2-0 file somewhere and add some appropriate text but am not sure. Can anyone advice or suggest a theme? Would it be easier to create my own theme, if so how?

Thanks
Jason

---

### Post by Knomefan on 2005-12-07
Hi, I think the easiest way would be to simply install the gnome-accessibility-themes.

I'm pretty sure there are themes available that fit what you want.

---

### Post by Brunellus on 2005-12-07
System>Preferences>Theme

There are some dark themes there.  I also prefer white-on-black for almost all of my computer work;  it makes things much easier on the eyes.

---

### Post by jaseywasey on 2005-12-08
Hello,
Thanks for the replies. I found the accessibility themes. They had the suffix DEB (debian???). I've googled about on this and again I can't find a answer to what I actually do with a deb file. I was expecting to find a tar/tgz file which I could extract to an appropriate location. I've gone into (from memory) system>>themes>>install themes and selected the .deb file and this is not accepted as a choice. I guess the deb file needs to be altered in some way to allow it to be installed into themes. Am I going about this in the wrong way.
Thanks
Jason

---

### Post by Gustav on 2005-12-08
You can install gnome-accessibility-themes either by using synaptic or type
```
sudo apt-get install gnome-accessibility-themes
```
in the terminal

You can install *.deb files by typing
```
sudo dpkg -i PACKAGE_NAME
```
in the terminal

---

### Post by jaseywasey on 2005-12-09
Thanks,
I'll give both a try for practice. I'm sure I can find a few alternatives for apt-get and a few for the dpkg method. apt-get and dpkg featured a lot in my recent fiddling with ubuntu. I'd assumed these were for applications and was looking for something different for the themes. I guess I'm still thinking like a windows user.

Jason

I will be buying a linux for idiots type book.

---

### Post by doclivingston on 2005-12-09
[QUOTE=jaseywasey]Thanks,
I'll give both a try for practice. I'm sure I can find a few alternatives for apt-get and a few for the dpkg method. apt-get and dpkg featured a lot in my recent fiddling with ubuntu. I'd assumed these were for applications and was looking for something different for the themes. I guess I'm still thinking like a windows user.
[/QUOTE]

In general, most themes aren't packages, however some of them are, including offical gnome accessability themes.

---

### Post by Gustav on 2005-12-09
[QUOTE=jaseywasey]Thanks,
I'll give both a try for practice. I'm sure I can find a few alternatives for apt-get and a few for the dpkg method. apt-get and dpkg featured a lot in my recent fiddling with ubuntu. I'd assumed these were for applications and was looking for something different for the themes. I guess I'm still thinking like a windows user.

Jason

I will be buying a linux for idiots type book.[/QUOTE]
If you have a choise, always use apt-get (or the synaptic package manager, it's easier) because then dependencies are automaticly resolved and you are sure not to install software that is incompatible to Ubuntu.

---

