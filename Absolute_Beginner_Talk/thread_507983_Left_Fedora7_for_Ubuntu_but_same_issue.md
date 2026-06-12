---
title: "Left Fedora7 for Ubuntu but same issue"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-07-23
Hi all,

 I have tried "last two weeks"  to migrate to open source. I just rid myself of Fedora7 since I can't browse anything with Java. My wife plays on Pogo and such so I really need this to get her over here from Windblows.  Problem is, same issue with Ubuntu. I just installed it a few minutes back and did all the updates, etc... I still can't browse or "use" Java related sites. I followed the instructions on linking the plugin, etc...but still won't work. Ubuntu is my last chance to stay with open source else it's back to the dungeon that is MS. Any help would be appreciated. 

 Thanks,

 Paul

---

### Post by FleetAdmiral74 on 2007-07-23
You can install Java from the repos, System - Administration - synaptic. I have had no problems with Java, so this should eventually work out for you.

---

### Post by gimpguy2000 on 2007-07-23
> **FleetAdmiral74 said:**
> You can install Java from the repos, System - Administration - synaptic. I have had no problems with Java, so this should eventually work out for you.

Hi and thank you, i'll try it right now. 

 Paul

---

### Post by FleetAdmiral74 on 2007-07-23
Also might try this, credit to [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

 How to install J2SE Runtime Environment (JRE) v6.0 with Plug-in for Mozilla Firefox

    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

    * When asked, agree with DLJ license terms. 

This doesn't work for amd64, since there's no 64-bit firefox plugin. A 32-bit firefox is necessary. Ubuntuforums provides special scripts for configuring some 32-bit applications in amd64.k

An alternative for amd64 is to use blackdown Java. However it is buggy and not all Java applications work. It is also a closed source application so no benefit can be derived from using it. It is the default Java application for distributions like Gentoo however.

sudo apt-get install j2re1.4-mozilla-plugin 

This installs blackdown Java.

---

### Post by gimpguy2000 on 2007-07-23
Thanks for the tips. The first suggestion didn't work so I am donwloading from link in second suggestion and hope that works. Thanks again for the help, i'll post back if it works or not. 

 TX

 Paul

---

### Post by bodhi.zazen on 2007-07-23
Hmm ....

Java is usually a snap to install and configure.

Can you describe your problem or error message better ?

Also for restricted formats see this link :

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Fedora is a great OS, but I think you will find the Ubuntu community if very accommodating to new users.

---

### Post by gimpguy2000 on 2007-07-23
Hi again, 

 No go. I don't get an install plugin pop up anymore but do get this... ** This error means Java (one of the technologies built into most browsers) is not working correctly on your browser.**

I have deleted cookies, etc...enabled all Java in Firefox. It did ask to allow the site and I did, but it still won't load a java game. 

 Thank you,

 Paul

---

### Post by gimpguy2000 on 2007-07-23
> **bodhi.zazen said:**
> Hmm ....

Java is usually a snap to install and configure.

Can you describe your problem or error message better ?

Also for restricted formats see this link :

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Fedora is a great OS, but I think you will find the Ubuntu community if very accommodating to new users.


 Hi, more accommodating? I am laughing because everywhere else, I simply got ignored or their knowledge thrown in my face basically. Of course there was one or two people that helped and I was grateful but the [B]Ubuntu community is FAR better, excellent so far. 
[/B]

 But back on track, thank you for the link, I am gathering as much info as possible as I can't get anything java to go. 

I apologize as well for not posting my specs:

 **HP pavil, 512 384 ram, intel chip, 120 WD gig  "non shared full use" with Ubuntu 7. **


TX

 Paul

---

### Post by gimpguy2000 on 2007-07-23
Hi,

 I can't install the restricted packages, I get this error :[B] E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

  This isn't looking good at all. I could live with it, but my wife likes her games and that's all she really does on the pc plus I don't want to have to keep boot switching between OSs. So that's why i'm so desperate to get this fixed. I want to keep open source, the programs are better, the fee is better, lol, and the community is better. Well, here at least :)

 Thanks again,

 Paul

---

### Post by LowSky on 2007-07-23
Are you using 64bit ubuntu? i think that is your problem... try ubuntu for x86 based processors.

512 384 RAM? Sorry but im confused about that.. or is it a HP pavillion 512 with 384 RAM?


Java should work very easily... go to add/remove progams, make sure you select all availible programs make sure you have mozilla java plugin 1.6 as well as java 6.0

---

### Post by benx009 on 2007-07-23
have you tried running dpkg --configure -a in the terminal?

---

### Post by perce on 2007-07-23
try opening a terminal (Applications > Accessories > Terminal) and type
sudo dpkg --configure -a

After that, try typing 
sudo apt-get install sun-java6-plugin

---

### Post by gimpguy2000 on 2007-07-23
> **LowSky said:**
> Are you using 64bit ubuntu? i think that is your problem... try ubuntu for x86 based processors.

512 384 RAM? Sorry but im confused about that.. or is it a HP pavillion 512 with 384 RAM?


Java should work very easily... go to add/remove progams, make sure you select all availible programs make sure you have mozilla java plugin 1.6 as well as java 6.0

 Hi,

 I downloaded for x86 not the 64. I did go to add/remove andselect the moz jav plug etc... that was actually the first thing I did. Then downloaded from the link, and manually linked the plugin. I have  a feeling if I look for the plugin link it will say damaged.  Maybe it's Pogo? Do you know of any other java based sites w\games I could try? 

 Thanks yet again,
 Paul

EDIT : sorry bout separation, not 512 RAM,  that's the model, I have 384 ram.

---

### Post by gimpguy2000 on 2007-07-23
Here is the run results from terminal... I ran fist command and got >

dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Second command>

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
gimpguy@gimpguy-desktop:~$ sudo apt-get install sun-java6-plugin
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


Update> After using manual edit>

dpkg: requested operation requires superuser privilege

---

### Post by perce on 2007-07-23
> **gimpguy2000 said:**
> Hi,
 Do you know of any other java based sites w\games I could try? 


Try this: 
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)
it's Sun's official test page (I think).

---

### Post by xubu_caapn on 2007-07-23
maybe the games aren't java after all, but shockwave? i don't know what games you're referring to, but it seems like you've tried everything, maybe that's the reason...

---

### Post by gimpguy2000 on 2007-07-23
Hi ,

 sorry for the wait, my son got hurt on his bike and when I came out of power down, the browser froze so I had to restart the system. 

 Ok, Java detected the 1.4 version and told me to donwload the 6u2 version for linux which i'm doing right now. It's the self extract not rpm and not X64. 

 Thanks,

 Paul

---

### Post by gimpguy2000 on 2007-07-23
Ok **Phew** latest update, same EXACT problems with Fedora...

Ok, I downloaded the Java package, I can't use the add\remove, it gives me same error as manual install, the E: error I mentioned above.  I can't get Java to even install which is the same problem I had in Fedora, even after changing permissions.  

  Well, same issue, same error in the browser. I don't get it honestly. I have tried everything possible. *sigh* .  I spent the last couple weeks trying to switch to an open source OS but it doesn't look like it's going to happen unless by some miracle Java gets noticed on my system by sites. 

 Oh, the Pogo games are Java and Flash\shockwave. I already installed the shock plug with no issues. Thanks for the suggestion though, if only it was that, lol. 

 Thanks again, 

 Paul

---

### Post by gimpguy2000 on 2007-07-23
Well, I have 6 installed as well as the plugin. So far nothing.

Even at the Java site, testing for Java, it won't detect it. ???  It still tells me to download latest version when I did and installed it. It even shows in synaptic as installed. 

 So as with Fedora, Java is on here, but can't be detected. And I did allow it in whitelist.  I don't understand at all what's going on and no one in my area knows linux so i'm not sure what to do. 

Aside from all that, I absolutely love the Ubuntu layout and ease of use! It's simply what we need to use an OS, no overbloat, very nice indeed. 

 Paul

---

### Post by EXCiD3 on 2007-07-23
What about installing Java through Automatix, I know ppl cant stand using it as it could break your system, but i have used it hundreds of times without any problems.

You can install Automatix here:[http://www.getautomatix.com/wiki/index.php?title=Installation]("http://www.getautomatix.com/wiki/index.php?title=Installation")

Plus it comes with easy installation of tons of other apps. ;)

**And by the way, it looks like the games at pogo.com are flash based games**

---

### Post by amoore on 2007-07-23
For a quick easy set up of JAVA and other restricted formats use AUTOMATIX!!!

You can get Automatix from [http://www.getautomatix.com/]("http://www.getautomatix.com/")

There will be some who dog Automatix but, for me it just works!

---

### Post by EXCiD3 on 2007-07-23
> **amoore said:**
> There will be some who dog Automatix but, for me it just works!

I agree with you, I personally have never had trouble with Automatix and recommend it to people all the time because its simplicity is awesome.

I think gimpguy2000 just needs to install Flash Player however, if you are talking about the games at [http://www.pogo.com]("http://www.pogo.com")...

---

### Post by Raineer on 2007-07-23
Need to back up just a bit, ok when people asked you to run these commands from a terminal:
```

sudo dpkg --configure -a
sudo apt-get install sun-java6-plugin

```
You came back and posted this:
```

dpkg: unknown option -o

```
What that means is that you didn't type the commands exactly as posted.  I believe the reason java isn't working is because your "automatic installer" or "apt-get" is hung on one simple package it can't resolve. The commands given above should correct this just fine.  Please try to run the suggested commands again and check your typing.

Also you posted that Ubuntu returned this:
```

dpkg: requested operation requires superuser privilege

```
All that means is you needed to add "sudo" to the beginning of whatever command you just ran. Along with installing java (sun-java6-jre), there is also the plugin for firefox (sun-java6-plugin). Resolving the initial "dpkg" issue should allow the updates and install to go through properly.

---

### Post by gimpguy2000 on 2007-07-23
Hi 

 Ok, If I can clear up what happened....

I copied and pasted the command  [B]  sudo dpkg --configure -a
sudo apt-get install sun-java6-plugin[/B]

 This still gave me the error with -o. I double checked as well seeing how that didn't fit. So finally I saw a little error message box on the bottom. It said the add\remove would not work and was locked and said to type this...

**sudo apt-get install -f**

 So I did this and I could add\remove again. Then I ran the install again, but it keeps saying it can't find package or not valid. So, I re-download as the RPM is giving errors and downloaded the self extractor again. 

 This time, I ran it in the Terminal, it installed, as well it states the v6 plugin is installed as well. It is now showing. HOWEVER, if I go to the Java site or pogo, etc... Java still isn't detected. 

 I re-ran the sudo dpkg--configure -a and still get the same error going to   -o. 

And a note: I did install the shockwave, the message I get is that JAVA is broken on pogo. 


This was the first code I was give:  sudo dpkg --configure -a <which is what I copied and pasted from 2nd page post, same as above or are there supposed to be spaces? I'll try your posted and see how it goes...BRB


 Thanks,

Mr. Confused

---

### Post by gimpguy2000 on 2007-07-23
Ok, ran this time but said current was already installed. So basically it's just not detected? It's all good on the system, just not from outside resources it seems. Now I am confused completely..:confused:

 Paul

---

### Post by gimpguy2000 on 2007-07-23
Verifying Java Version

Oops! You don't have the recommended Java installed.
Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.  

 This from Java???

---

### Post by EXCiD3 on 2007-07-23
Take a min to install Automatix...Seriously dude, it should take care of everything for you. I was so impressed when i first used it, i started installing it first thing everytime i reinstall Ubuntu.

---

### Post by wolfen69 on 2007-07-23
and the people cry out- **AUTOMATIX!!!!!!!**

---

### Post by gimpguy2000 on 2007-07-23
Hi I did use that already, "automatix"  it did it the first time, however. I downloaded it again just to be sure, ran it, opened the plugins and sure enough, the plugin is installed. 

I should state here that I have in fact tried everything suggested and apologize for not stating that sooner. 

 Thanks again,

 Paul

---

### Post by gimpguy2000 on 2007-07-23
I am not sure but I have a 4 port wired linksys router w\nat, would this block java ? 


 Paul

---

### Post by EXCiD3 on 2007-07-23
I really doubt that would cause it...but i dunno

---

### Post by EXCiD3 on 2007-07-23
Just found this link: [http://ubuntuforums.org/showthread.php?p=1174435]("http://ubuntuforums.org/showthread.php?p=1174435")

Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64, but its for the 64 bit versions...

---

### Post by gimpguy2000 on 2007-07-23
So basically what it boils down to then is, I can't use open source softare\OSs? I highly doubt it's the PC as that shouldn't affect it. I will try a couple more simple things I suppose before I uninstall Ubuntu. 

 This truly stinks "for me" of course since I really do like Ubuntu. Well, if no one has any more thoughts or suggestions, by later tonight, i'll be doing away with it. 

 I appreciate the help anyway. 

 Paul

EDIT, I didn't see the above post, i'll look at it first, THANK YOU!

---

### Post by EXCiD3 on 2007-07-23
Hey, man, don't give up on Ubuntu. You might try reinstalling and using Automatix off the bat to install it. I have used it every time, and make sure you install the Firefox extensions...Or you could try a different flavour of Ubuntu, like Kubuntu...I just hate for you to give up...Just promise me you won't use Windows.

---

### Post by Brian96 on 2007-07-23
> **gimpguy2000 said:**
> So basically what it boils down to then is, I can't use open source softare\OSs? I highly doubt it's the PC as that shouldn't affect it. I will try a couple more simple things I suppose before I uninstall Ubuntu. 

 This truly stinks "for me" of course since I really do like Ubuntu. Well, if no one has any more thoughts or suggestions, by later tonight, i'll be doing away with it. 

 I appreciate the help anyway. 

 Paul

EDIT, I didn't see the above post, i'll look at it first, THANK YOU!

When I first installed Ubuntu I ran into some flaky problems and ended up uninstalling in frustration. A few days later I found solutions to my issues and wound up reinstalling after all.

If you like the OS otherwise, maybe you can let it settle in for a few days and see if a solution emerges. The fact that this also occurred in Fedora is suspicious. But I would certainly give it a few days and see if a solution emerges. I personally feel that there should be a solution. Java has worked out-of-the box for me (all I did was install the packages already described in this thread). The only times I've had trouble with Java (and flash) was with Opera. People that know more may be able to help you dig a little deeper to find out what is the snag.

One more suggestion: You may want to start a new thread on this with a title that highlights the problem more specifically to attract the attention of anyone with more specific knowledge of Java. JMO

---

### Post by gimpguy2000 on 2007-07-23
> **EXCiD3 said:**
> Hey, man, don't give up on Ubuntu. You might try reinstalling and using Automatix off the bat to install it. I have used it every time, and make sure you install the Firefox extensions...Or you could try a different flavour of Ubuntu, like Kubuntu...I just hate for you to give up...Just promise me you won't use Windows.



 LOL, I don't have much choice but to use Windblows at this point, lol. I wish I could promise that, believe me. It's not just Ubuntu i'm giving up on but Fedora and Kubuntu, I tried all 3 all same issues with Java, I just don't get it and Ub was my last resort "ALTHOUGH" would be my ** first** choice NOW knowing how nice it is.  

 There has to be some reason the Java is not seen on my system by outside resources. 

I did try last suggestion, didn't do anything , same issue. I just don't get it, the links are not broke as they were in Ku and Fed, but still, same, very same issue, this is bothering me. However, I can't keep my wife off the pc forever , lol. So it looks like i'll be reverting back to the DARK PLACE. :(


 Thanks again,

 Paul

---

### Post by gimpguy2000 on 2007-07-23
> **Brian96 said:**
> When I first installed Ubuntu I ran into some flaky problems and ended up uninstalling in frustration. A few days later I found solutions to my issues and wound up reinstalling after all.

If you like the OS otherwise, maybe you can let it settle in for a few days and see if a solution emerges. The fact that this also occurred in Fedora is suspicious. But I would certainly give it a few days and see if a solution emerges. I personally feel that there should be a solution. Java has worked out-of-the box for me (all I did was install the packages already described in this thread). The only times I've had trouble with Java (and flash) was with Opera. People that know more may be able to help you dig a little deeper to find out what is the snag.

One more suggestion: You may want to start a new thread on this with a title that highlights the problem more specifically to attract the attention of anyone with more specific knowledge of Java. JMO

 I just may do that, re-post. As I stated in my upper reply, my wife does need to use the pc too "I gues" lolll. So I have to do something and fast. :( 


 Thanks,

 Paul

---

### Post by Brian96 on 2007-07-23
> **gimpguy2000 said:**
> I just may do that, re-post. As I stated in my upper reply, my wife does need to use the pc too "I gues" lolll. So I have to do something and fast. :( 


 Thanks,

 Paul

Definitely want to keep the wife happy. And if she's been deprived of her games for 2 weeks she may be getting antsy. ;)

Any troubleshooting I could do would be wild shots in the dark, but Java problems are not common fare on a default Ubuntu install once the appropriate packages are installed, so there seems to be something peculiar about your system.

---

### Post by treadwayms on 2007-07-23
might try a new post along the lines of     Pogo.com, Is it possible to play the games via Ubuntu? just a thought as I would make the switch also but like you my wife plays there a lot. Although I have 2 pc's :)

---

### Post by Brian96 on 2007-07-23
> **treadwayms said:**
> might try a new post along the lines of     Pogo.com, Is it possible to the games via Ubuntu? just a thought as I would make the switch also but like you my wife plays there a lot.

I think Gimpguy's problems are more specific to his setup. He not only has trouble on pogo.com but also on the Java test site. My Ubuntu install works fine on the Java site (and with all other Java-enabled sites I have tried) unless I am using Opera as my web browser (but Ubuntu uses Firefox by default). I haven't tried pogo.com specifically (don't want to sign up for an account--I don't have time to let it suck me in!), but I doubt that is his problem.

As I said earlier, most of us get Java to work in a very straightforward manner. Gimpguy seems to have some specific issues, and I am following this thread closely to see if the community is able to help him find a solution.

---

### Post by gimpguy2000 on 2007-07-24
Hi all, well, i'm on.. ....w...w...w...win win win dow...s       ooooh I hate saying that!  I am on my son's pc since my wife booted to Windows for , yup, pogo.   I just don't know what else to do. Why on all the open source OS's? Is MS paying the darn sites to reject it or what? The reason I thought my router because I can't set it up in *NIX versions.  The Java cache is keeping the whitelists just fine so there is some interraction. Pogo changes the applet every time so Java warning pops up but won't allow, nor from Java site. My files were hidden by default and I enabled them but didn't matter. There are no broken links, etc... I may reinstall , I don't know.  

 I am getting fed up with open source OSs , if not for you people being so helpful, it would have been gone by now so **to the Ubuntu site/software owners/makers... give these fourm people a round of applause, they deserve it. **

 Paul

---

### Post by Brian96 on 2007-07-24
Did you post a new thread on this yet? A title like "JAVA Problem" may attract more focused attention. I know when I scan thread titles I only lock onto stuff I've had experience with. I only found this thread because I was thinking about trying Fedora and was curious what issue you had.

---

### Post by treadwayms on 2007-07-24
Well I take back what I said , I went to pogo.com and played about 5 various online games they all worked fine for me :) So maybe I can talk the wife into switching hmmmm

---

### Post by stchman on 2007-07-24
> **gimpguy2000 said:**
> Hi all,

 I have tried "last two weeks"  to migrate to open source. I just rid myself of Fedora7 since I can't browse anything with Java. My wife plays on Pogo and such so I really need this to get her over here from Windblows.  Problem is, same issue with Ubuntu. I just installed it a few minutes back and did all the updates, etc... I still can't browse or "use" Java related sites. I followed the instructions on linking the plugin, etc...but still won't work. Ubuntu is my last chance to stay with open source else it's back to the dungeon that is MS. Any help would be appreciated. 

 Thanks,

 Paul

So she plays online games that use a JRE.  No problem.  Follow this:


sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin

You need the plugin for java to work in a browser.

I play checkers and chess on Yahoo games.

---

### Post by gimpguy2000 on 2007-07-24
Hi stchman,

 Thanks for the reply. I tried that but unfortunately it didn't work. There is another who just installed Ubuntu, an admin at a Gimp site and he has the same issue, so there must be a common issue. There were others in Fedora as well with this and when I had Fedora which is why I migrated to Ubuntu. I don't know what else to do. 

 TX

 Paul

---

### Post by stchman on 2007-07-25
> **gimpguy2000 said:**
> Hi stchman,

 Thanks for the reply. I tried that but unfortunately it didn't work. There is another who just installed Ubuntu, an admin at a Gimp site and he has the same issue, so there must be a common issue. There were others in Fedora as well with this and when I had Fedora which is why I migrated to Ubuntu. I don't know what else to do. 

 TX

 Paul

All the java site I go to work fine using FIrefox.  I don't know what to say.  So you are having problems with websites that use imbedded Java?

---

### Post by Raineer on 2007-07-25
Well if it is insisting you have only JRE 1.4.2, it may mean that your path is setup to that installation.

See, Linux can run many different versions of Java without a hitch, it just depends which is currently being pointed out in your $PATH

```
$PATH
```
at a command line might show something like "/usr/java/jre.1.4.2" instead of "/usr/java/jre.6.0.2" which I think is the most current.

You might just type 
```
ls /usr/java
``` so we can see what directories and installations are actually there.

If that is correct, we could remove the offending installation (by removing it's directory) and possibly fix the whole thing by:
```
PATH=$PATH:/usr/java/jre.6.0.2
export PATH

```

Just a thought, it's something I have had to do when working with multiple versions on purpose.

---

### Post by gimpguy2000 on 2007-07-25
Thanks for the hint, you know I was wondering the same thing because everything was pointing to 1.4  even though 6 was installed. I just did a reinstall of my system so I want to see how it goes. Start new ya know so I know what I muck up this time. 

 TX 

 Paul

---

### Post by trent dillman on 2007-07-25
...

---

### Post by gimpguy2000 on 2007-07-25
Hi, ok, mine says this from first line code 

```
lrwxrwxrwx 1 root root 24 2007-07-24 22:08 /etc/alternatives/java -> /usr/bin/gij-wrapper-4.1
```

You want I should download 6? And how would you think best, by add\remove or manual? 

TX

OOPs:  RPM or SE?

---

### Post by trent dillman on 2007-07-25
...

---

### Post by gimpguy2000 on 2007-07-25
> No such file or directory

 TX

 Paul

---

### Post by trent dillman on 2007-07-25
...

---

### Post by gimpguy2000 on 2007-07-25
```
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bash: syntax error near unexpected token `('

```

 :(:(:confused:

---

### Post by trent dillman on 2007-07-25
...

---

### Post by Raineer on 2007-07-25
Typically that means you have Synaptic or Update Manager open when you are trying to run "apt-get" commands from the shell. Linux has a "lock" function to keep 2 programs from trying to act on the same files.

---

### Post by gimpguy2000 on 2007-07-25
Well that's what I thought too, however, I don't have anything open :confused:  Let me check system resources and see what's running in there quickly.

---

### Post by gimpguy2000 on 2007-07-25
Nada :(

---

### Post by trent dillman on 2007-07-25
...

---

### Post by kvonb on 2007-07-25
This thread is starting to look like the 3 stooges meets keystone cops with Homer Simpson thrown in for good measure!

OK, have a look at the included screenshot.

From your main menu (I'm ASSuming you are using Gnome desktop, NOT KDE!), click on Applications and down the bottom you will see: Add/Remove...", select that.

Now at the top RHS of the add/remove window, you will see the word "show" and a box to the right of it, drop that box and select "All available applications".

Now at the top left, in the box marked "Search" type "java" (without the quotes!), and after a few seconds you should see something similar to my screenshot.

Now simply make it look like mine, ie untick ALL the Java 1.4 guff, then select the ones I have, then click on OK at the bottom.

Now it should remove the old 1.4 rubbish and install the later one.  During the download process, you might have to click on "show details" as it might be waiting for you to accept an agreement.

Now it may be wise to reboot at this stage, I know it's a Windows thing to do, but it could avoid potential issues.

Now, when you get back to the desktop, open a terminal (menu->Accessories->Terminal) and copy and paste the following into it:

```
sudo update-alternatives  --config java
```That will give you a list of ALL the installed versions on your system and you can       select the one you want!

Hope that fixes your problems.

Regards, Kev :)

---

### Post by gimpguy2000 on 2007-07-25
Yup, that did it :) It's going now...

50%

40 sec left 20, 19, 18

unpacking

DONE....awaiting instruction  :) :) I have a good feeling about it this time..

---

### Post by rajeev1204 on 2007-07-25
Hmm KVONB is right

try that command in terminal 

 sudo update-alternatives  --config java


I had a similar issue with another application and selecting sun java version will solve the issue .

---

### Post by gimpguy2000 on 2007-07-25
java-6-sun  java-6-sun-1.6.0.00

from the li /usr/lib/jav

---

### Post by gimpguy2000 on 2007-07-25
Alriggghhtty then...it's working in the terminal this time...I select 2 or 1?        

  ```
   1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

```

I assume 2 but want to make sure

oops, thanks rajeev1204

---

### Post by kvonb on 2007-07-25
> **gimpguy2000 said:**
> Alriggghhtty then...it's working in the terminal this time...I select 2 or 1?        

  ```
   1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

```I assume 2 but want to make sure

oops, thanks rajeev1204

Number 2 sir!

Here is what mine has:

```
kev@kev:~$ update-alternatives  --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default
[*], or type selection number:
```

---

### Post by gimpguy2000 on 2007-07-25
**ALLRIIGHHHTTTTTT YAHOOOOOOO!!!!** 

[B] After two weeks it's working!!!!!!! YES!!!  Here's a small party for the Ubuntu forum people!! You guys are the BEST! 


[/B]=r:)=;:-({|=:lolflag:):P:guitar::KS:popcorn:


**[SIZE="6"]Honestly I can't thank you enough! [/SIZE]**


 Paul


**Thanks Kvonb for waiting through this tonight, I appreciate it!! Your method finally did it!! **

---

### Post by kvonb on 2007-07-25
You are most welcome, save a few beers for me ;)

I'm sure everyone did their part, I only know what I know from these forums and the great and helpful people here.

---

### Post by gimpguy2000 on 2007-07-25
Most definitely, **every one** who helped! Yep, like I said before, just this forum is a reason to stay with Ubuntu, that's the only reason I did stay with it after this Java issue, now i'm glad I did...

** Thanks all again! **

 Consider drinks saved! :)

---

### Post by Brian96 on 2007-07-25
> **gimpguy2000 said:**
> ALLRIIGHHHTTTTTT YAHOOOOOOO!!!!

After two weeks it's working!!!!!!! YES!!!  Here's a small party for the Ubuntu forum people!! You guys are the BEST! 





Honestly I can't thank you enough!


 Paul


Thanks Kvonb for waiting through this tonight, I appreciate it!! Your method finally did it!! 

Whew! I'm glad you got that worked out. Now on to the endless tinkering I was talking about! ;)

---

### Post by gimpguy2000 on 2007-07-25
I t has already begun, lolll. 

TX again,

 Paul

---

