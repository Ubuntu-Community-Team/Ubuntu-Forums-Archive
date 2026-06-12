---
title: "Java runtime 6 environment step-by-step installation!"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by loverman210 on 2007-11-29
Hi everyone! 

I am a total newbie and I need your help!
I have simple question: How do I install Java runtime 6 environment on ubuntu 7.10??

I have tried solutions provided on other posts but I have been confused by the different ways....Could you tell me what to do like I am a 6-years old child??

---plz the child doesn't want to use automatix!- just wants to do this the traditional way!-and learn by the way!!

Thanx in advance!!

---

### Post by kpkeerthi on 2007-11-29
Applications -> Accessories -> Terminal.
Then, paste
```

sudo apt-get install sun-java6-jre sun-java6-fonts

```
and press <enter>

If you also need Java browser plugin, use
```

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```
instead

---

### Post by RomeReactor on 2007-11-29
Hi. Look for **sun-java6-jre** in Synaptic (System->Administration->Synaptic); or open a terminal (Applications->Accessories->Terminal) and paste:
```
sudo apt-get install sun-java6-jre
```
then press ENTER. It will ask for your password.

EDIT: Late again...

---

### Post by Anicka on 2007-11-29
Hi!

In my experience you need to used a text-based installation procedure (=not synaptic). Type into the terminal (you find it in the menu applications -> accessories)```
sudo apt-get install sun-java6-plugin
``` It is dependent on all the necessary packages to run java applets in firefox including sun-java6-jre. There will be a licence agreement form that pops up in your terminal window. Use your (I don't remember exactly) arrow-keys or tab to move the cursor to the <ok> bottom and press enter.

Good luck with installing!

---

### Post by loverman210 on 2007-11-29
I did everything you said and the terminal says that everything is already installed - nothing added - removed or modified! But the thing is that when I go to java.com and click on the "verify installation" I t keeps poping up a message sayng that I have 1.4.2 and not 1.6!! - so I guess the right question is how do I enable java on firefox?? (it is activated in the settings menu already!-)

---

### Post by Mze on 2007-11-29
Bring up the terminal:

sudo update-alternatives config--java 

Select the java version you want to use

---

### Post by kpkeerthi on 2007-11-29
-- dup post deleted --

---

### Post by loverman210 on 2007-11-29
> **Mze said:**
> Bring up the terminal:

sudo update-alternatives config--java 

Select the java version you want to use

that is what pops up when I issue the vcommand you are saying:

"update-alternatives: unknown argument `config--java'"

---

### Post by Mze on 2007-11-29
Command screw up:

Try this:

sudo update-alternatives --config java

---

### Post by loverman210 on 2007-11-29
> **Mze said:**
> Command screw up:

Try this:

sudo update-alternatives --config java

Ok! that worked...for the selection part...but nothing happened!! --The terminal reports that I am using version 1.6 update 3 and also there is an application listed at applications>internet>Sun java 6 web start!!

Everything seems to be enabled except maybe the plugin working with firefox!!

help....don't know what else to do....[[IMG]http://img206.imageshack.us/img206/7999/pictestsl0.png[/IMG]](http://imageshack.us)

---

### Post by vetruven on 2007-11-29
Regarding your browser - you need to change the plug-in in your Firefox accordingly.
I took it from the java site [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)
>  Mozilla 1.4 and later

   1. Go to the plugins sub-directory under the Mozilla installation directory
      cd <Mozilla installation directory>/plugins
   2. In the current directory, create a symbolic link to the JRE ns7/libjavaplugin_oji.so file Type:
      ln -s <JRE installation directory>/plugin/i386/ns7/libjavaplugin_oji.so

      Example:
          * If Mozilla is installed in this directory:
            /usr/lib/mozilla-1.4/
          * and if the JRE is installed at this directory:
            /usr/java/jre1.5.0
          * Then type at the terminal to go to the browser plug-in directory:
            cd /usr/lib/mozilla-1.4/plugins
          * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
            ln -s /usr/java/jre1.5.0/plugin/i386/ns7
            /libjavaplugin_oji.so .
   3. Start Mozilla browser or restart it if it is already running. Note that if you have other Mozilla components (ie: Messenger, Composer, etc) running, you will need to restart them as well.
   4. Go to Edit > Preferences. Under Advanced category > Select Enable Java


---

### Post by da_excelsior on 2007-11-29
i triied installing using

sudo apt-get install sun-java-jdk6


but am getting some broken link error...


excelsior@excelsior-desktop:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (= 6-03-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-03-0ubuntu2) but it is not installable
E: Broken packages

---

### Post by Mze on 2007-11-29
Please run Anicka's command in the terminal

Source: [Java - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Java#head-7f353d2f3fb1a09aac09cf1caee565e897319306")

---

### Post by loverman210 on 2007-11-29
> **vetruven said:**
> Regarding your browser - you need to change the plug-in in your Firefox accordingly.
I took it from the java site [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

done that...still the same!

---

### Post by loverman210 on 2007-11-29
> **Mze said:**
> Please run Anicka's command in the terminal

Source: [Java - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Java#head-7f353d2f3fb1a09aac09cf1caee565e897319306")

this one refers to x64....I am using core 2 duo 32bit!

Do you know any way of uninstalling and reinstalling again java??

---

### Post by Mze on 2007-11-29
fire up Synaptic Package Manager

Search for Java

Select the modules you installed, "Right Click" and choose "Remove". "Apply" changes. Close Synaptic.

Fire up the Terminal and "copy and paste" commands already suggested by others.

Hope this helps.

---

### Post by loverman210 on 2007-11-29
It's unbelievable! I am the only person in the world who can't install java!! - I have tried everything you said but still...no results!! - When I type about:plugins on firefox, it shows that I have java 1.6.3 installed...but that's all!! It will not use it!! I will use 1.4.2 no matter what I do!! any ideas? - any terminal commands??

---

### Post by quandary on 2007-11-29
i don't know what you did change by now, but normally if you have a newer version then the version already installed, you type:

apt-get upgrade PACKET_NAME

so just try upgrade on the plugin...

---

### Post by penguinv on 2007-11-29
> **Mze said:**
> Command screw up:

Try this:

sudo update-alternatives --config java

And it said:

There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.

Java from the webpage only offered Manual. 
When I downloaded and opened could not install.

OK.
And for me, this all started with Azurus.

---
The need for Java!

---

### Post by Mze on 2007-11-30
Don't know why you are having a hard time installing the Java runtime environment on your end. Was pretty straight forward for me using this [guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox"). (I'm using Feisty)

---

### Post by loverman210 on 2007-11-30
I have some new info now...

Yesterday I managed to install Azureus 2.5.0.4 and everything worked great! In the "about" tab it reported using java 1.6.0_03!! So...I think everything is cool here...BUT firefox insists not to be using the 1.6 plugin!! any new ideas?


@Mze: I read your guide - Sadly, nothing I haven't  tried till now....:(

---

### Post by Mze on 2007-11-30
The only thing I can come up with is that Firefox has it's libjavaplugin.so file symbolically linked to the Java 1.4 libjavaplugin.so file.

Run a search for the file **libjavaplugin.so** using the command "Places" >>> "Search for files".
Look in Folder >> change to File System

From the search results, find the libjavaplugin.so found in the directory /usr/lib/mozilla/plugins
Select and Right click>>Open Folder. Right click again on the libjavaplugin.so file. Click on "Properties". It should show how your file is symbolically linked. If yours is linked to the Java 1.4 then that may be the problem.

My file has a symbolic  link to /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin.so

So, if your file has a symbolic link to the java 1.4 folder then, you'd have to change that.

Below should be your syntax to get your Mozilla libjavaplugin.so file to link to the java6 file:

Fire up terminal:

cd /usr/lib/mozilla/plugins 
ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin.so

Make sure Java option is set in Firefox. Open up Firefox, go to the Java site and test your version of Java.

Hope this fixes your problem.

Cheers

---

### Post by MozartlovesUbun2 on 2007-11-30
good, i was looking for a step by step java installation.

================================

but it's still confusing with the firefox plugins, also Miro keeps crashing with firefox on

can someone make it a bit clearer, thanks

---

### Post by Mze on 2007-11-30
Since you're using Gutsy:

The unofficial [Ubuntu Guide for Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") suggests using >>>
sudo apt-get install sun-java6-plugin

---

### Post by radimatt on 2007-11-30
I am indeed running Gutsy (with Firefox), and have been unable to get Java working, despite trying all the suggestions, including uninstalling everything Java-related and then starting from step 1.

When I open a page that uses Java, a bar pops up on the top of, saying that I need to install missing plugins.  When I select Java 6 to try and install it as recommended, an error message says that  Sun-Java6-Plugin is already installed.  If it's already installed, then why does Firefox not recognize it?

Thanks for this thread.  It's a piece of help on a tough issue.

---

### Post by stevemu on 2007-11-30
I had a lot of trouble along these lines as well.  In the end I got it to work when I installed:

icedtea-java7-bin
icedtea-java7-jre
icedtea-java7-plugin

Using Synaptic.

---

### Post by MozartlovesUbun2 on 2007-12-01
> **stevemu said:**
> I had a lot of trouble along these lines as well.  In the end I got it to work when I installed:

icedtea-java7-bin
icedtea-java7-jre
icedtea-java7-plugin

Using Synaptic.

ok cool, is icedtea an open version of java?

would you recommend this

(i thought java was open source now, am i mistaken?)

---

### Post by Lord DarkPat on 2007-12-01
help!!!!!! Whenever I install Java, the package breaks at sun-java6-bin, and it messes up the whole adept database. It will refuse to add/remove anything!!! I had to keep re-installing Kubuntu 5 times!!!!! And don't think I'm joking cuz I ain't. Any help?

---

### Post by SunnyRabbiera on 2007-12-01
I also have a method:
this is an easy fix (sorta),
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

### Post by Lord DarkPat on 2007-12-01
> **SunnyRabbiera said:**
> I also have a method:
this is an easy fix (sorta),
first you go to the java website:
[here]("http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com")

after that download the self extracting file (dont bother with the RPM, its not worth your time)
after that is done downloading go to where you downloaded your file (if all your files download to the desktop though, please take the file to your home folder or something, just open up your home directory and drag and drop.)
after this you will need to open up synaptic again
now what you will need is something called nautilus-open-terminal, as this will allow you to open a terminal inside your desired directory (for some odd reason this is not enabled in ubuntu, it honestly should be)
now after installing it you will have to restart your session... there is no real easy way to do this bit I am afraid.
now after restart go to whatever directory you put the java installer in and under "file" in the menu go to "open in terminal"
after this type in:
sudo sh jre-6u3-linux-i586.bin
now you will have to go through the license junk of java, just keep on pressing space until it asks
Do you agree to the above license terms? [yes or no]
its annoying to get to it, but just type in "yes" and all will be fine
after the installation is done just close the terminal (it will say done after its completed)
Thanx for ur help, but....a........
I use *_[U]K_[/U]*ubuntu
i.e. No nautilus, no synaptic
yes dolphin, yes adept.
Thanx neways

---

### Post by SunnyRabbiera on 2007-12-01
> **Lord DarkPat said:**
> Thanx for ur help, but....a........
I use *_[U]K_[/U]*ubuntu
i.e. No nautilus, no synaptic
yes dolphin, yes adept.
Thanx neways

well its still possible to do this in kubuntu too, most of the steps are the same:
first you go to the java website as i said before
after that download the self extracting file (dont bother with the RPM, its not worth your time)
after that is done downloading go to where you downloaded your file (if all your files download to the desktop though, please take the file to your home folder or something, just open up your home directory and drag and drop.)
now in dolphin go to "tools" then to "open terminal"
go to whatever directory you put the java installer in
after this type in:
sudo sh jre-6u3-linux-i586.bin
now you will have to go through the license junk of java, just keep on pressing space until it asks
Do you agree to the above license terms? [yes or no]
its annoying to get to it, but just type in "yes" and all will be fine
after the installation is done just close the terminal (it will say done after its completed)

its practically the same thing, the only reason why I said most of that is for the usual ubuntu user.
kubuntu is roudabout the same thing, its just in the default gnome of ubuntu the nautilus terminal app is missing.
now if any Xubuntu users have any issues well:
when you open your home directory or wherever you installed the file to just right click on a empty space and select "open terminal here"
after that its all the same deal as both above:
type in:
sudo sh jre-6u3-linux-i586.bin
now you will have to go through the license junk of java, just keep on pressing space until it asks
Do you agree to the above license terms? [yes or no]
its annoying to get to it, but just type in "yes" and all will be fine
after the installation is done just close the terminal (it will say done after its completed)

---

### Post by loverman210 on 2007-12-02
@Mze:

Done exactly what you said and found out that -sadly in this case- the link of the plugin is java 6....

anyway my friend thank you very much for all the effort, I appreciate it...and the willingness of everyone to help me out here...I may be better off with java...who knows..

thanks again!

---

