---
title: "Help!! Javascript 1.5 &amp; Firefox Issues!!!"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by shannon.cummins on 2006-07-21
I have Ubuntu DD 6.06 and the included firefox browser installed.  When I log into my Webtycho classes I get an error saying I do not have Javascript 1.5 installed for my browser.  How do I fix this error.  This error can be recreated by going to the following link

[https://tychousa6.umuc.edu/sys/browserinfo.html](https://tychousa6.umuc.edu/sys/browserinfo.html)

Any help would be greatly appreciated.  It reports that i have JS 1.4 installed.  Thanks in advance

PS  I have searched the forums and documentation for answers on this and can find nothing.

---

### Post by slimdog360 on 2006-07-21
a number of ways to solve this problem. Easiest way is to use automatix, just search the forums. 
The other way is to do it by hand, in the folder where you unpacked java there should be a plugins folder. In that there is a file which you have to copy into the mozilla folder. Proper instructions are on the sun java website.

---

### Post by geco on 2006-07-21
> **shannon.cummins said:**
> I have Ubuntu DD 6.06 and the included firefox browser installed.  When I log into my Webtycho classes I get an error saying I do not have Javascript 1.5 installed for my browser.  How do I fix this error.  This error can be recreated by going to the following link

[https://tychousa6.umuc.edu/sys/browserinfo.html](https://tychousa6.umuc.edu/sys/browserinfo.html)

Any help would be greatly appreciated.  It reports that i have JS 1.4 installed.  Thanks in advance

PS  I have searched the forums and documentation for answers on this and can find nothing.

on firefox
```

about:plugins

```

search for
```

Java(TM) Plug-in 1.5.0_06-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_06

```

from terminal, verify you java installation
```

dpkg -l *java* | grep ii

```

if not installed:
```

sudo apt-get update

```

```

sudo apt-get install sun-java5-jre

```
for proprietary java package

or
```

sudo apt-get install free-java-sdk

```
for free java

EDIT:
you can also do (from terminal)
```

locate libjavaplugin_oji.so

```
to search for java plugin.
if it is somewhere **link** it to firefox
```

sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox/plugins

```
if you have java installed, probably "/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/" is the right path.

---

### Post by shannon.cummins on 2006-07-21
Installed automatix, and it installed the JRE 1.5 successfully (so it said) but when I start my browser and do the check it still says JavaScript 1.4.  I also cannot use my webtycho classroom environment and get the popup stating I need JS 1.5.  What did  I do wrong??

---

### Post by steve.horsley on 2006-07-21
Installing a java VM won't change the javascript version. Javascript is built into firefox. And firefox 1.5.0.4 (the current version) implements javascript 1.5. What version of firefox do you have (menu Help->About Mozilla Firefox)?

If you mean java and not javascript then geco gave you an answer:
use **locate libjavaplugin_oji.so** to verify the correct library file name and then use this command (it's all one line):
```
sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox/plugins
```

---

### Post by shannon.cummins on 2006-07-22
Here is what I have as far as FF goes

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.4) Gecko/20060608 Ubuntu/dapper-security Firefox/1.5.0.4


Everything that geco told me to do was completed successfully and when I created the links they were created and verified in the correct folders.  here is what the verification page at [https://tychousa6.umuc.edu/sys/login.html?http://tychousa6.umuc.edu/WebTycho.nsf&0](https://tychousa6.umuc.edu/sys/login.html?http://tychousa6.umuc.edu/WebTycho.nsf&0) says


Item  	             Value  	            Compatible
Type 	             Netscape (Netscape Gecko Engine version 20060608) 	N/A
Version 	     5 	                    No
Cookies Enabled      Yes 	            Yes
Java Enabled 	     Yes 	            Yes
Java Vendor 	     Sun Microsystems Inc.  N/A
Java Version         1.5.0_07               Yes
JavaScript Version   1.4 	            No
The following information is for use when contacting WebTycho Support.
Platform 	     UNIX 	            N/A
User Agent 	     Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.4)        Gecko/20060608 Ubuntu/dapper-security Firefox/1.5.0.4 	N/A
Default Language 	en-US 	N/A
Flash Player Version 	Flash Not Installed 	N/A


Everything that we said above to do was successful (so it seemed) but the version number stays at 1.4.  What do you think the issue could be, I am stumped.

---

### Post by steve.horsley on 2006-07-22
Solved!

Using the version of firefox that installs with Ubuntu, that page tells me (as it does you) that I'm using javascript version 1.4.

However, if I use the same version of FF downloaded and installed from [www.mozilla.com](www.mozilla.com) then that page tells me I am compatible and using javascript 1.5. 

In my opinion this is really bad of the Ubuntu folks. They are issuing a downgraded browser with the same version number as the real thing. I have no idea why they do it, but they deserve a slap.

You need to download the **real** firefox from [www.mozilla.com](www.mozilla.com) and install that. 
* Download the file (a tar.gz)
* extract it: **tar xf filename**
* copy the folder to /opt: **sudo cp -r firefox /opt**
* clean up by deleting the download and extract if you want
* Edit your launcher to launch /opt/firefox/firefox instead of that rubbish fake.

---

### Post by Thorndeux on 2006-07-22
Ubuntu is a very stable linux release. In order to achieve this, as I understand, new versions of applications are only offered when it is verified that they work flawlessly with the system.
I don't think it's fair to rant about the developers who are doing all the work for you. In fact, I think it's shameless, sorry. There are articles in the wiki explaining how to upgrade firefox, there are tons of threads about it in all different kinds of forums. You have to put some work and time in to solve those kinds of problems.
If you want all the latest programs run debian unstable and you'll see how far you get.

Cheers,
Thorn

---

### Post by shannon.cummins on 2006-07-22
Good to know.  Steve, it worked!  Thanks for all of your help.  I agree with you though, the version number of FF should not match the latest if it is not.  But again, I am not one of the hard working individuals that are putting their time and effort into this product (of which I think is excellent).  Thank you for everyones help, and I am sure I will need more in the future.  Now if I see this issue on this forum again I can help the next new guy.

---

### Post by steve.horsley on 2006-07-22
> **Thorndeux said:**
> Ubuntu is a very stable linux release. In order to achieve this, as I understand, new versions of applications are only offered when it is verified that they work flawlessly with the system.
I don't think it's fair to rant about the developers who are doing all the work for you. In fact, I think it's shameless, sorry. There are articles in the wiki explaining how to upgrade firefox, there are tons of threads about it in all different kinds of forums. You have to put some work and time in to solve those kinds of problems.
If you want all the latest programs run debian unstable and you'll see how far you get.

Cheers,
Thorn


Yes the Ubuntu guys do a grand job. But why downgrade Firefox with an earlier javascript version, and **then claim** it's Firefox 1.5.0.4? It isn't. And you can't claim it's just about security updates - release notes for FF1.5 state javascript 1.6, so Ubuntu must have downgraded that before releasing Dapper. They have caused this poster problems. I bet the web site says you need JS 1.5+ and also says FF1.5 is one of the browsers that **does** work. 

If they're going to downgrade it then fine, but they shouldn't then claim it's what it isn't any more.

---

### Post by breakthestate on 2006-07-24
I have to use WebTycho for courseware as well, and I have to admit that when I upgraded to Dapper and it told me JavaScript 1.5 wasn't configured and I couldn't see this and I couldn't see what I needed to see, I freaked out a little, but when I found this forum thread,, it helped me figure it out.

I thank everyone for their directions above, but I wanted to give step by step directions as they worked for me in case anyone couldn't quite make sense of the above.  Below are the step by step instructions that worked for me:


1.  Open web browser.  Got to [www.getfirefox.com/]("http://www.getfirefox.com/")

2.  Click on the link to download the file.  It will be called something like firefox-1.5.0.4.tar.gz.

3.  Download the file to your home directory and then open up a terminal by pressing alt + F2.  When the "Run Application" dialog comes up type "xterm" and click "Run."  All the text in boxes with the word "Code:" above them represent the text you should be typing in your xterm.

4.   I made a directory called webtycho to put the new version of firefox in.  Then I moved the file that I downloaded into the directory.
```

mkdir webtycho
mv /downloadLocation/firefox-1.5.0.4.tar.gz $HOME/webtycho
``` 
5.  Then I changed into the webtycho directory and decompressed the tarball.

```
cd $HOME/webtycho
tar xvzf firefox-1.5.0.4.tar.gz
``` 
6.  This command should produce another directory in your webtycho directory named firefox.

7.  Now here is where reading the above posts can get you confused.  JavaScript and Java are separate things.  I suggest a quick Wikipedia search for more information.  Essentially, if you have not installed the JDK or JRE and you don't care to do so, skip this step.  The JRE is what allows your computer to use the fancy java-based text editor.  If you have installed a JRE or JDK, and you want Java to be enabled on this version of firefox and thus want to be able to use the "fancy" WebTycho text editor, make a symbolic link in your $HOME/webtycho/firefox/plugins folder.

```
cd $HOME/webtycho/firefox/plugins
ln -sv /usr/lib/firefox/plugins/libjavaplugin.so
``` 
8.  Now make sure all copies of the Ubuntu version of firefox are closed.  (At least I found this necessary).

```
killall firefox-bin
``` 
9.  Now change into your $HOME/webtycho/firefox/ folder and run the program:

```
cd $HOME/webtycho/firefox/
./firefox&
``` 
10.  Hopefully this worked for you.  I do note that if you want to use the Ubuntu version of firefox, you will have to close out of "your" version first.  I'm sure there is a work around for this, but I don't care enough to look into it.  I'm just glad I've yet again avoided booting XP!

Is there a way to edit the subject line of this thread to take out the exclamation points and possibly add the word WebTycho so it would be easier to find?

Thanks,

Jeff

---

### Post by breakthestate on 2006-07-24
Also see [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) for a more complete set of directions for installing new firefox.  My solution is definitely quick and dirty, but again, it at least sets you up to work immediately.  

- jeff

---

### Post by daemacles on 2007-12-30
As it pertains to webtycho, they just have some old buggy javascript code that mis-identifies a browser's javascript version.  Workaround and further explanation found at [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/156882](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/156882)

---

