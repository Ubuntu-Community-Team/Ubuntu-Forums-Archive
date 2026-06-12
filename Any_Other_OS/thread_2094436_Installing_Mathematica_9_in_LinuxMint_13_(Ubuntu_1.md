---
title: "Installing Mathematica 9 in LinuxMint 13 (Ubuntu 12.04)"
date: 2012-12-13
forum: Any Other OS
---

### Post by rewyllys on 2012-12-13
Two years ago this month, I reported here on my experience in installing Mathematica 8 in Linux ([http://ubuntuforums.org/showthread.php?t=1636057](http://ubuntuforums.org/showthread.php?t=1636057)).

Now I can report on installing Mathematica 9 in Linux.

The best thing to report is that this installation went even more smoothly than my previous one.  This time I simply followed the current installation instructions on the Wolfram Research Website: [http://support.wolfram.com/kb/10652](http://support.wolfram.com/kb/10652)

Mathematica 9 for Linux downloads as a script file:  Mathematica_9.0.0_LINUX.sh  
I used the default locations in the script in installing it on my desktop, but it would have been easy to change to other locations if I had wanted to do so.

The installation script concludes with a hyperlink to instructions for activating the new installation: [http://reference.wolfram.com/mathematica/tutorial/ActivatingMathematica.html](http://reference.wolfram.com/mathematica/tutorial/ActivatingMathematica.html)  
I had no trouble with the activation (well, that is, once I started using my Activation Key for Mathematica 9 rather than the outdated Key for my Mathematica 8 installation:rolleyes:).

---

### Post by dwsmith on 2013-03-18
I followed their advice as well but with no luck.  The download is downloads so throught the terminal

cd ~/Downloads
sudo sh ./installer.sh
sh: 0: cant open ./installer.sh

What do I need to do?

---

### Post by rewyllys on 2013-03-19
Have you examined the Properties of installer.sh?

To do so, right-click on installer.sh and choose Properties. In the Properties window, click on the Permissions tab.  In the Permissions window, make sure that the box labelled "Allow executing file as program" is checked.

Close the Permissions window, and try again the commands you listed in your question.  This time "sudo sh ./installer.sh" should work.

---

### Post by dwsmith on 2013-03-21
> **rewyllys said:**
> Have you examined the Properties of installer.sh?

To do so, right-click on installer.sh and choose Properties. In the Properties window, click on the Permissions tab.  In the Permissions window, make sure that the box labelled "Allow executing file as program" is checked.

Close the Permissions window, and try again the commands you listed in your question.  This time "sudo sh ./installer.sh" should work.

I had to call it as Mathematica_9.0.1_LINUX.sh for it to install

---

### Post by rewyllys on 2013-03-23
> **dwsmith said:**
> I had to call it as Mathematica_9.0.1_LINUX.sh for it to install
I take it that you succeeded in installing Mathematica 9.0.1.  Glad to hear that.

Did the activation process go smoothly for you?

---

### Post by lomakez on 2013-03-27
Here detailed written installation mathematica in pictures (site in Russian) 
[http://kobriniq.ru/mathematica/ustanovka-mathematica-9-v-operatsionnoy-sisteme-linux-os-mint-ubuntu](http://kobriniq.ru/mathematica/ustanovka-mathematica-9-v-operatsionnoy-sisteme-linux-os-mint-ubuntu)

---

