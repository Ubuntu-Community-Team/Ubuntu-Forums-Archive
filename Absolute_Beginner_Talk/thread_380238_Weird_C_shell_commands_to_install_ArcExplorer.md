---
title: "Weird C shell commands to install ArcExplorer"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by LLivingLarge on 2007-03-09
Can someone explain this to me?

From [http://www.esri.com/software/arcexplorer/download9.html](http://www.esri.com/software/arcexplorer/download9.html)

```
Additional installation steps for UNIX and Linux
Setting up your account for UNIX and Linux

ESRI recommends that you execute ArcExplorer from a C shell. The following instructions are for a C shell environment setup.

To use ArcExplorer after installation, add the following lines to your .login or .cshrc file:
setenv AEJHOME /ArcExplorer
set path = ( $path $AEJHOME/bin )

To enable the changes, type:
% source <.login or .cshrc>

Editing the user $HOME/aimsclient.properties file

Copy the aimsclient.properties file from the $AEJHOME/Xenv directory to your user $HOME location. Update the value of the WebBrowser key in the aimsclient.properties file to point to the location of your default browser. Update the value of the AEJavaHelp key in the aimsclient.properties file to point to the location of the ArcExplorer online Help files.

Starting ArcExplorer for UNIX and Linux

With $AEJHOME/bin included in your PATH, start ArcExplorer by typing: aejava
```

---

### Post by x1a4 on 2007-03-10
Hi,

Install either *csh* (the BSD C Shell) or *tcsh* (the Tennex C Shell) or better still, both.  

*sudo apt-get csh tcsh*

I recommend you use *tcsh* (what I use by default) which has more features.  

Start the shell: 

*tcsh -l*

Change the Current Working Directory (CWD) to your home directory: 

*cd ~*

Open _~/.cshrc_ for editing: 

*nano ~/.cshrc*

Add these lines to _~/.cshrc_: 

[B]setenv AEJHOME /ArcExplorer
set path = ( $path $AEJHOME/bin )[/B]

Exit *nano*

To enable the changes, type:

*source ~/.cshrc*

> Copy the aimsclient.properties file from the $AEJHOME/Xenv directory to your user $HOME location.

$HOME is a variable which holds the location of your home directory
eg: /home/LLivingLarge  

$AEJHOME is a variable holding the path to ArcExplorer
$AEJHOME/Xenv is the path in which the file _aimsclient.properties_ resides

Copy the file: 

*cp ${AEJHOME}/Xenv/aimsclient.properties ~/aimsclient.properties*

> Update the value of the WebBrowser key in the aimsclient.properties file to point to the location of your default browser.
Update the value of the AEJavaHelp key in the aimsclient.properties file to point to the location of the ArcExplorer online Help files.

Open _~/aimsclient.properties_ for editing: 

*nano ~/aimsclient.properties*

Look in the _aimsclient.properties_ file and change the **WebBrowser** and **AEJavaHelp** keys to the full path of your favourite browser and ArcExplorer online help files. 

If you're using GNOME, set **WebBrowser** to _/usr/bin/gnome-www-browser_.  
If you're using Xfce, set **WebBrowser** to _/usr/bin/xfbrowser4_.  
Otherwise, set **WebBrowser** to _/usr/bin/sensible-browser_.
This way you won't have to change this should you change default browsers.  

Set **AEJavaHelp** to wherever you have AEJava documentation.  Most likely somewhere in _/usr/share/doc_. 

Exit *nano*

> Starting ArcExplorer for UNIX and Linux
With $AEJHOME/bin included in your PATH, start ArcExplorer by typing: aejava

You've already added $AEJHOME/bin to your path in _~/.cshrc_ which means you just have to run

*aejava*

If you have problems running *aejava* from TCSH (doubtful) run *csh -l* then from within the C Shell *aejava*.

---

### Post by Starks on 2007-03-14
Hmm, got past that hurdle... Now a new one.

Exception in thread "main" java.lang.NoClassDefFoundError: com/esri/ae/AE

---

### Post by Starks on 2007-03-14
> **Starks said:**
> Hmm, got past that hurdle... Now a new one.

Exception in thread "main" java.lang.NoClassDefFoundError: com/esri/ae/AE

Never mind, I figured it out.

---

### Post by x1a4 on 2007-03-14
> **Starks said:**
> Never mind, I figured it out.

May I ask how?  

BTW edit your original post and tick the 'issue is resolved' checkbox.

---

### Post by gus sett on 2007-03-15
search on shell explain for more info :arrow: 

> **LLivingLarge said:**
> Can someone explain this to me?

From [http://www.esri.com/software/arcexplorer/download9.html](http://www.esri.com/software/arcexplorer/download9.html)

```
Additional installation steps for UNIX and Linux
Setting up your account for UNIX and Linux

ESRI recommends that you execute ArcExplorer from a C shell. The following instructions are for a C shell environment setup.

To use ArcExplorer after installation, add the following lines to your .login or .cshrc file:
setenv AEJHOME /ArcExplorer
set path = ( $path $AEJHOME/bin )

To enable the changes, type:
% source <.login or .cshrc>

Editing the user $HOME/aimsclient.properties file

Copy the aimsclient.properties file from the $AEJHOME/Xenv directory to your user $HOME location. Update the value of the WebBrowser key in the aimsclient.properties file to point to the location of your default browser. Update the value of the AEJavaHelp key in the aimsclient.properties file to point to the location of the ArcExplorer online Help files.

Starting ArcExplorer for UNIX and Linux

With $AEJHOME/bin included in your PATH, start ArcExplorer by typing: aejava
```

---

### Post by michaeljb2005 on 2007-03-24
> **Starks said:**
> Hmm, got past that hurdle... Now a new one.

Exception in thread "main" java.lang.NoClassDefFoundError: com/esri/ae/AE

Please do clarify how you solved this.  This is the only thing I have a problem with as well.

---

### Post by MaskedMarauder on 2007-03-26
I just installed a 6.10 ubuntu.  There is no csh or tcsh and they don't appear to be in the standard repositories.

Does anyone know which repositories need to be added to the master list to get these packages?

---

### Post by x1a4 on 2007-03-26
> **MaskedMarauder said:**
> I just installed a 6.10 ubuntu.  There is no csh or tcsh and they don't appear to be in the standard repositories.

Does anyone know which repositories need to be added to the master list to get these packages?

Universe.

---

