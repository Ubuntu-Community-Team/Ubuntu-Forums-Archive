---
title: "Can't Start Limewire - Suspect Java Runtime Problem"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by pushin50 on 2008-01-31
Hey Nice People,

Hope someone can help with this. I'm running gutsy in the gnome environment. Have also tried some of steps below in kde desktop. This desktop is hardwired as the server for a Belkin wireless router using DSL modem for internet . Two wireless laptops hanging off the network - dhcp enabled. Previously had no issues running Limewire in XP (which, by the way, is gone forever, good riddance). Ubuntu is just so SANE and USABLE! - like civil compared to common law. But I digress . . .

Here's the history:

1st) Downloaded Limewire 4.16 from Limewire site. First time, opened with gdebi package installer. Limewire installed fine but, when I ran it for first time, hung on the "Limewire loading" splash screen at 6%. Tried uninstalling, dowloading the Limewire deb package and installing by clicking that open. Same result.

2nd) After a lot of reading, looked at Java and installed Sun-Java6. Tried to run Limewire from terminal. Limewire configures and recognizes Java but just hangs. Terminal says this:

     dad@daddad-desktop:~$ limewire
     Starting LimeWire...
     Java exec found in PATH. Verifying...
     Suitable java version found [java = 1.6.0_03]
     Configuring environment...
     Loading LimeWire:

Again, however, Limewire hangs at 6%.

3rd) Limewire website recommends jre 5. Using Synaptic Manager, uninstalled Java6 jre and installed Java5 jre. Tried Limewire with Java5 jre. Same result but different looking splash screen. Re-installed Java6 jre from Synaptic. Currently, everything I can see in the system tells me Java6 runtime is installed and active. Checked Java control and verified Java enabled. Checked Firefox and verified Java enabled.

4th) Found .limewire folder, cleared it and tried a new Limewire install. Still hangs at 6% load with no error message in terminal.

5th) Ran the Java version verification from Java website. It says, Oops! You don't have most recent version; running 1.4 of the runtime environment.

6th) Knowing that I do, in fact, have most recent Java 1.6.0_03, per terminal read-out above, I think, OK let's enable Java per instructions of Java website. So, thinking I can link Mozilla to correct jre version and using the terminal, I successfully run the following commands set out in the instructions on the Java website:

     cd /usr/lib/mozilla/plugins

     sudo ln -s usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so

These commands appear to run fine.

However, I verify again using applet from Java website with same result - runtime out of date at 1.4. Again, Limewire, run from terminal, finds suitable Java version, returns no errors, configures and starts loading. Same as output listed at 2nd point above. Again, hangs with splash screen showing 6%.

It feels to me like there is either a path error or a conflict in Java runtime versions. I'm stuck. 

BTW, no apparent issues with Firefox. 

Any thoughts? I will be forever grateful.

Chris

---

### Post by emarkd on 2008-01-31
You can certainly have more than one version of java on your system at once, so I'm not sure this is your problem.  However, have you installed the ubuntu-restricted-extras package from Synaptic?  I think that's got the newer version of that plugin in it.  May'be it would help.

---

### Post by asmoore82 on 2008-01-31
check out [http://www.frostwire.com/](http://www.frostwire.com/)
:guitar:

---

### Post by SunnyRabbiera on 2008-01-31
I had an issue like this myself, sadly there is no real easy way to resolve it:
first you go to the java website:
[here]("http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com")
after that download the self extracting file (dont bother with the RPM, its not worth your time)
after that is done downloading go to where you downloaded your file (if all your files download to the desktop though, please take the file to your home folder or something, just open up your home directory and drag and drop.)
after this you will need to open up synaptic
now what you will need is something called nautilus-open-terminal, as this will allow you to open a terminal inside your desired directory (for some odd reason this is not enabled in ubuntu, it honestly should be)
now after installing it you will have to restart your session... there is no real easy way to do this bit I am afraid.
now after restart go to whatever directory you put the java installer in and under "file" in the menu go to "open in terminal"
after this type in:
sudo sh jre-6u3-linux-i586.bin
now you will have to go through the license junk of java, just keep on pressing space until it asks
Do you agree to the above license terms? [yes or no]
its annoying to get to it, but just type in "yes" and all will be fine
after the installation is done just close the terminal (it will say done after its completed)

---

### Post by tanderson on 2008-01-31
I had a problem on a machine a while ago trying to get frostwire to run. It had the free version installed and decided to go with the sun version. I could never get it to run the sun version. I found the java "executable" in /usr/bin and found it was a symbolic link and proceeded to chase the symbolic links all over the hard drive and manually changed the link that was wrong. After this my java problems were over. Well....I shouldn't say that, java is one big problem as far as I am concerned.

---

### Post by pushin50 on 2008-02-01
Thanks Folks,

Ran SunnyRabierra's instructions to the letter. Same result:

dad@daddad-desktop:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading LimeWire:

Hangs with splash screen showing 6% loaded. Even after hard re-boot.

Installed ubuntu-restricted-extras as suggested by emarkd. Same result.

I had tried Frostwire previously but, after these changes, tried again. As before, running frostwire from terminal returned this:

dad@daddad-desktop:~$ frostwire 
Starting FrostWire... 
Java exec found in PATH. Verifying... 
Suitable java version found [java = 1.6.0_03] 
Configuring environment... 
Loading FrostWire: 
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct 
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct 
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct 
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct

Sorry, should have mentioned that in first post but forgot.

Also should have mentioned that I have tuned off "Visual Effects" in Preferences/Appearance.

Maybe I'm missing fonts these apps are trying to load?

Thanks for your help.

Chris

---

### Post by pushin50 on 2008-02-01
Here's a little more info.

dad@daddad-desktop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

---

### Post by pushin50 on 2008-02-01
OK Folks,

Linux wins again!

Took me a while but I found gtk-gnutella and what a nice, fast, easy piece of work it is!

Still haven't gotten Limewire of Frostwire working but, really, who cares?

Thanks to those who helped.

Lesson learned: there's a better answer within Linux and those genius repositories - every time!

:)

---

