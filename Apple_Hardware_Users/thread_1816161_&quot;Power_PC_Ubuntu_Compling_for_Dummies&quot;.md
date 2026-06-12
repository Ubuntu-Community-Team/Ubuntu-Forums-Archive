---
title: "&quot;Power PC Ubuntu Compling for Dummies&quot;"
date: 2011-08-01
forum: Apple Hardware Users
---

### Post by MacPenguin1972 on 2011-08-01
Hello,

I am quoting a response from another user from another thread I posted because this response for me has created another question in my mind - about compiling.

This was a response from Tylerjd on how to compile a program like Seamonkey to the Power PC Ubuntu. But I would like to know if this can be used for other programs that are "intel only" using the source code? 

Also, where can someone like me who has no programming skills (except a very basic laughable HTML page maybe?) learn more about compiling programs like this?

And finally - for Mac OS 10.4 Tiger II know this is an Ubuntu forum but we're using Macs right? I use both Tiger and Ubuntu on my Power Mac) -- since OS X is unix-based, are there similar compiling techniques for programs on the Mac OS X side as well? Like can I port an Ubuntu program I like or another open source program I like to Tiger using Apple's console?

Thank you in advance for any replies. I appreciate any assistance you can render, and I want to try this with Sea Monkey and see what happens. :-)

Here's the quote:


> **Tylerjd said:**
> You do have a point in that last sentence. 

You don't need to be a programmer to compile a program. 

Generally speaking you need to know four commands that you would run in  the terminal. (this could be used as a great learning experience)

The first thing you need to do is to get the source, which is usually in  a tar.gz format. Let us take Seamonkey as an example (as Firefox seems  to be all pre-configured for specific architectures. The source would be  found [here]("http://www.seamonkey-project.org/releases/#source").
It comes packaged as a .tar.bz2, which is like a tar.gz. Download it into your downloads folder.

When it is finished, goto the area that you downloaded it and double  click to extract it.  It should be extracted into a seamonkey-2.2  folder. Then open terminal.

In terminal, use the command cd to goto the folder, so your command  would be something along the lines of (replace the seamonkey-2.2 to  whatever the you extracted the tar.bz2 to)
```
cd Downloads/seamonkey-2.2/
```Which brings you into the directory where the seamonkey source is located. 

These next commands may seem scary at first, but only the last one does  anything that may be hard to undo to your system- that being installing  seamoney. You'll see what I mean.

Time to compile the code. _Make sure to reread this a few times before you do anything in order to have an understanding of what you are doing_

First, you will need to make sure you have all of your tools. As it  seems like you have never compiled anything before, you will need to  install the developer tools required to install.

In the following code boxes, don't type anything in the parentheses. Those are comments telling you what the command is doing. 
```
sudo apt-get install build-essential (Installs the developer  tools. You will need to enter the password associated with your account)
(Wait for that to finish, make take some time depending on internet connection)

./configure (Makes sure you have all of the required dependancies to  build seamonkey. If it says that it fails, google the step that it  failed on, see if there is a package that you can install that will  resolve it, then run the command again)
(It will look like a lot of scary code, but it is nothing to worry about.)

make (yes, a very simple command, and that is all of the hard work,  which is compiling the actual program. Your CPU will be used a lot, and  it may take some time to finish the process, so go grab a coffee.)(if  this step fails, then post back here)


sudo make install 
(this last command (make install) installs the program, and you will  need to enter your password again)
```And that is all that is to it.  Seamonkey should show up under applications, and if not just run the  command "seamonkey &" in terminal

---

### Post by pauljwells on 2011-08-02
One of the most useful ways of compiling software for the powerpc is to make use of the ppa repositories. You'll find many of these mentioned in the forums where developers can upload newer versions of packaged programs or programs that are not officially available in Ubuntu, or where there is some issue that prevents automatic builds, for example a dependency is missing.
Since Ubuntu is only officially supported for x86 architectures, if a developer submits code to a ppa it is only automatically built for x86 (and x64) and so no packages appear in Synaptic for users of other architectures.
However, the source code is available and it includes all the necessary 'extras' to make deb installer packages so that once installed you can use Synaptic to view, uninstall whatever and all the program files go into the right places.
To compile a package is easy, let's say you want to compile the program 'foo'. Firstly you need to install the necessary build packages:

```
sudo apt-get install build-essential fakeroot dpkg-dev
```

Then make a new directory to work in and cd into it

```
mkdir foo-build
cd foo-build
```

Add the required ppa repository to your repository list and update

```
sudo add-apt-repository ppa:foo
sudo apt-get update
```

then download the source

```
apt-get source foo
```

This will download and extract the source code tree. Once complete there will be a new subdirectory in your build directory, cd into it:

```
cd foo-version-etc
```

You need to make sure you have all the dependencies installed:

```
sudo apt-get build-dep foo
```

Then the clever bit:

```
dpkg-buildpackage -rfakeroot -b
```

(If you have a multi-core machine you can speed up the build by adding a 'jobs' flag: ```
dpkg-buildpackage -rfakeroot -b -j4
```

Have a cup of tea. When the compilation is finished cd back up to the build directory:

```
cd ..
```

There you will (if all went well) find one or more 'deb' files, which you install with:

```
sudo dpkg -i ./*.deb
```

I only learned this a few months ago and now it's second nature. I found it on this site:

[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/]("http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/")

I found some of the steps used on that site were unneccesary and some of the 'sudo' use was unneccessary too so my method is a little neater.

For some packages I have found that sometimes you have to build some of the dependencies too. You just have to run through this same process for the dependency first.

I regularly use this process for the unity-2d ppa and for vlc on powerpc.

---

### Post by pauljwells on 2011-08-02
There is a ppa for seamonkey here

[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa")

you would obviously replace all the 'foos' in my post with 'seamonkey' :-D

I would say that seamonkey is going to be complex and it's possible that there could be 'hiccups' in the build. Don't be put off, but try something known to work first (like the unity-2d packages, which are worth installing anyway on powerpc) to get the hang of it before you start hacking...

---

### Post by rsavage on 2011-08-02
Thanks pauljwells, will try this out!

---

### Post by MacPenguin1972 on 2011-08-03
Hello,

Thank you for the information on that SeakMonkey thing, I will definitely put that to use.. But not just SeaMonkey - I am trying to find out wher I can learn general compiling techniques so that I can do this for pretty much any Linux program I want to run on Ubuntu, if possible.

"Learning to fish" rather than just asking for a fish.  I am interested in any books or websites or even threads on the subject.

Thanks again. :-)

---

### Post by pauljwells on 2011-08-03
Compiling is (if the dev did his work properly) a no-brainer...

```
./configure
make
sudo make install
```

is really all there is to it!

Packaging is a little more complex, but compiling a package is also easy (see my post above)

Some more complex programs use 'cmake' which is a turbocharged configure system for dealing with different architectures, but again is quite straightforward - the programs that use it will give you detailed instructions.

The fun starts when you start to hack, after all, why compile if there's already a package available? I started because on powerpc some stuff doesn't work but can be made to work with (fairly) simple fixes. The hard part isn't usually making the fix but finding the broken code.

My personal advice: learn python! (other codes are available...)

---

### Post by rsavage on 2011-09-10
MacPenguin1972, I don't know if you've tried any of this yet, but I had a go at compiling Firefox using pauljwells' excellent post.  I think I am right in thinking that getting the latest Firefox sparked your interest in this?

Admittedly, I didn't use a powerpc machine, but I don't think that matters.

The various ppa for firefox are explained here [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) .

I've copied the exact commands I used.  You can see how they follow pauljwells post.

```

sudo apt-get install build-essential fakeroot dpkg-dev
mkdir firefox-build
cd firefox-build
sudo add-apt-repository ppa:mozillateam/firefox-stable 
sudo apt-get update
apt-get source firefox
cd firefox-6.0.2+build2+nobinonly
sudo apt-get build-dep firefox
dpkg-buildpackage -rfakeroot -b
cd ..
sudo dpkg -i firefox_6.0.2+build2+nobinonly-0ubuntu0.11.04.1_amd64.deb

```I also tried compiling Firefox 7 and Firefox 9.  These proved more troublesome, but I succeeded in the end.  The compiling failed with a nondescript error and this is where the "skill" of compiling lies.  So I did what every man does in this situation..... hit google of course with the error.  Took me a while to find it, but I think I had actually run out of memory!  I increased my swap, tried it again and bobs your uncle! 

Whilst compiling, the memory usage as determined by system monitor was mostly around 500MB.  With no applications loaded it is usually about 360MB (using standard ubuntu).  At some point during compiling though it must exceed 2GB.  Therefore, I suggest your combined swap + memory must be something like a minimum of 2.5GB.  If you're lowish on physical memory then possibly you could boot into single user mode without a GUI to conserve memory?

It took a few hours to compile and I could see for some people with a slower processor it would be an all nighter!  It also uses 5GB of hard drive space.  Yes that is 'GB'!

More info about compling firefox can be found here [https://developer.mozilla.org/En/Simple_Firefox_build](https://developer.mozilla.org/En/Simple_Firefox_build) .

I didn't really need to compile firefox, I just did it to see if I could.  It pretty much worked exactly as it should of.   I think there is a quicker way to get Firefox into powerpc lucid and maverick using apt-pinning, but if you want the novelty of compiling it yourself then I say go for it!

---

### Post by pauljwells on 2011-09-10
> **rsavage said:**
> using pauljwells' excellent post

I Can't tell you how happy it makes me to read this! :-)

---

### Post by rsavage on 2011-09-11
> **pauljwells said:**
> I Can't tell you how happy it makes me to read this! :-)

I say it like I see it!  Only I think I've spotted an error in both our posts!  After you add a ppa you need to do a "sudo apt-get update" I think.  I've now edited my post.....

---

### Post by canhoto on 2011-11-03
> **pauljwells said:**
> One of the most useful ways of compiling software for the powerpc is to make use of the ppa repositories. You'll find many of these mentioned in the forums where developers can upload newer versions of packaged programs or programs that are not officially available in Ubuntu, or where there is some issue that prevents automatic builds, for example a dependency is missing.
Since Ubuntu is only officially supported for x86 architectures, if a developer submits code to a ppa it is only automatically built for x86 (and x64) and so no packages appear in Synaptic for users of other architectures.
However, the source code is available and it includes all the necessary 'extras' to make deb installer packages so that once installed you can use Synaptic to view, uninstall whatever and all the program files go into the right places.
To compile a package is easy, let's say you want to compile the program 'foo'. Firstly you need to install the necessary build packages:

```
sudo apt-get install build-essential fakeroot dpkg-dev
```Then make a new directory to work in and cd into it

```
mkdir foo-build
cd foo-build
```Add the required ppa repository to your repository list and update

```
sudo add-apt-repository ppa:foo
sudo apt-get update
```then download the source

```
apt-get source foo
```This will download and extract the source code tree. Once complete there will be a new subdirectory in your build directory, cd into it:

```
cd foo-version-etc
```You need to make sure you have all the dependencies installed:

```
sudo apt-get build-dep foo
```Then the clever bit:

```
dpkg-buildpackage -rfakeroot -b
```(If you have a multi-core machine you can speed up the build by adding a 'jobs' flag: ```
dpkg-buildpackage -rfakeroot -b -j4
```Have a cup of tea. When the compilation is finished cd back up to the build directory:

```
cd ..
```There you will (if all went well) find one or more 'deb' files, which you install with:

```
sudo dpkg -i ./*.deb
```I only learned this a few months ago and now it's second nature. I found it on this site:

[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)

I found some of the steps used on that site were unneccesary and some of the 'sudo' use was unneccessary too so my method is a little neater.

For some packages I have found that sometimes you have to build some of the dependencies too. You just have to run through this same process for the dependency first.

I regularly use this process for the unity-2d ppa and for vlc on powerpc.
And if you want to find a certain package's source, how do you find it's ppa, or a ppa for it?

---

### Post by pauljwells on 2011-11-04
> **canhoto said:**
> And if you want to find a certain package's source, how do you find it's ppa, or a ppa for it?

Google? :-D

You only need the ppa source if you want a program that's not in the standard repos or you want an updated version. Not all programs have ppas of course.

---

### Post by canhoto on 2011-11-06
> **pauljwells said:**
> 

```
sudo apt-get build-dep foo
```


I tried to do this with Firefox 7.0.1, but I got the following error:
> The following packages have unmet dependencies:
 libcurl4-openssl-dev : Depends: libldap2-dev but it is not going to be installed
E: Build-dependencies for firefox could not be satisfied.


What to do?

---

### Post by pauljwells on 2011-11-06
> **pauljwells said:**
> 
For some packages I have found that sometimes you have to build some of the dependencies too. You just have to run through this same process for the dependency first.

Usually you get the error you are seeing because there is no ppc version of the library available in any repo, so you have to build it yourself. Just create a new build directory and run through the process for the dependency first and then you can go back to the main Firefox build.

You should be able to download the source for the dependency directly with ```
apt-get source foo
``` without needing a ppa version.

---

### Post by canhoto on 2011-11-07
> **pauljwells said:**
> Usually you get the error you are seeing because there is no ppc version of the library available in any repo, so you have to build it yourself. Just create a new build directory and run through the process for the dependency first and then you can go back to the main Firefox build.

You should be able to download the source for the dependency directly with ```
apt-get source foo
``` without needing a ppa version.

Thank you.

I tried that with first with Libreoffice and it had the same dependency issue: it asked for libldap2dev, but when trying to install it, it said that I have libldap-2.4-2_2.4.23-0ubuntu3.6 and I should have libldap-2.4-2_2.4.23-0ubuntu3.5.

Do you know how to solve this?

---

### Post by canhoto on 2011-11-07
> **canhoto said:**
> Thank you.

I tried that with first with Libreoffice and it had the same dependency issue: it asked for libldap2dev, but when trying to install it, it said that I have libldap-2.4-2_2.4.23-0ubuntu3.6 and I should have libldap-2.4-2_2.4.23-0ubuntu3.5.

Do you know how to solve this?

Never mind. I just downgraded it.

Sorry!

---

### Post by pauljwells on 2011-11-07
Cool! You have to accept that you're living on the bleeding edge trying to compile FF7 on PPC. The problem with downgrading is that sometimes you might have a package installed that depends on the later version, then you're into looking through change logs and hacking your own versions...
It's pretty satisfying when it works isn't it? ;-)

---

### Post by canhoto on 2011-11-08
> **pauljwells said:**
> Cool! You have to accept that you're living on the bleeding edge trying to compile FF7 on PPC. The problem with downgrading is that sometimes you might have a package installed that depends on the later version, then you're into looking through change logs and hacking your own versions...
It's pretty satisfying when it works isn't it? ;-)
I began compiling libreoffice, and the computer has been working on that for almost 24 hours! It has also taken already 5.0 GB of space. I can delete it after installing the program, I hope?

---

### Post by rsavage on 2011-11-08
Hey canhoto, well done!  It will be cool if you got it compiled.  I should imagine libreoffice is pretty big and so is going to take a long time!!!  Once you have the deb you'll be able to safely delete the 5GB+ that the compiling took up.

---

### Post by canhoto on 2011-11-08
> **rsavage said:**
>    I think there is a quicker way to get Firefox into powerpc lucid and maverick using apt-pinning, but if you want the novelty of compiling it yourself then I say go for it!

What's this apt-pinning thing?

Btw, I'm still waiting for Libreoffice to finish building, after more than 24 hours! Is it normal?

I have no memory problems, but the CPU usage (I've a 1,6 Ghz processor) is at 100%.

---

### Post by rsavage on 2011-11-09
100% cpu usage for compiling is normal.  It is trying to get it done as fast as possible.  Are things still changing on the screen?

You can look up the build logs for packages in ubuntu.  The libreoffice one is here [https://launchpad.net/ubuntu/+source/libreoffice/1:3.4.3-3ubuntu2/+build/2816135](https://launchpad.net/ubuntu/+source/libreoffice/1:3.4.3-3ubuntu2/+build/2816135) .  It took 9 hours, but I have no idea if that was on some sort of powerpc super computer.  Speed of compiling is very much determined by the specs of your computer.  For example, if it is using swap memory then it is going to take much longer.

Apt-pinning is described here  [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) .  You may also like to read about backporting [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports).  I did have a play around with this a few months ago, it might all come back to me if you struggle with it.  From what I remember the documentation was a little flakey.

---

### Post by MacPenguin1972 on 2011-11-09
> **pauljwells said:**
> One of the most useful ways of compiling software for the powerpc is to make use of the ppa repositories. You'll find many of these mentioned in the forums where developers can upload newer versions of packaged programs or programs that are not officially available in Ubuntu, or where there is some issue that prevents automatic builds, for example a dependency is missing.
Since Ubuntu is only officially supported for x86 architectures, if a developer submits code to a ppa it is only automatically built for x86 (and x64) and so no packages appear in Synaptic for users of other architectures.
However, the source code is available and it includes all the necessary 'extras' to make deb installer packages so that once installed you can use Synaptic to view, uninstall whatever and all the program files go into the right places.
To compile a package is easy, let's say you want to compile the program 'foo'. Firstly you need to install the necessary build packages:

```
sudo apt-get install build-essential fakeroot dpkg-dev
```Then make a new directory to work in and cd into it

```
mkdir foo-build
cd foo-build
```Add the required ppa repository to your repository list and update

```
sudo add-apt-repository ppa:foo
sudo apt-get update
```then download the source

```
apt-get source foo
```This will download and extract the source code tree. Once complete there will be a new subdirectory in your build directory, cd into it:

```
cd foo-version-etc
```You need to make sure you have all the dependencies installed:

```
sudo apt-get build-dep foo
```Then the clever bit:

```
dpkg-buildpackage -rfakeroot -b
```(If you have a multi-core machine you can speed up the build by adding a 'jobs' flag: ```
dpkg-buildpackage -rfakeroot -b -j4
```Have a cup of tea. When the compilation is finished cd back up to the build directory:

```
cd ..
```There you will (if all went well) find one or more 'deb' files, which you install with:

```
sudo dpkg -i ./*.deb
```I only learned this a few months ago and now it's second nature. I found it on this site:

[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)

I found some of the steps used on that site were unneccesary and some of the 'sudo' use was unneccessary too so my method is a little neater.

For some packages I have found that sometimes you have to build some of the dependencies too. You just have to run through this same process for the dependency first.

I regularly use this process for the unity-2d ppa and for vlc on powerpc.



Hi Paul,

I forgot about this thread and just re-found it. 

This is very helpful. I hope to mess around with this once I reinstall Ubuntu 10.10 on my system after this whole fiasco with 11.10, 12.04, etc. (I won't be touching those again - too much headache)

Can these techniques be used for pretty much any program? Like replacing "foo" with the name of the program you wish to compile?

This is the kind of thing I was looking for on my other threads - command line codes to compile, or upgrade to new versions of Ubuntu, etc. I am trying to get away from defective install discs once I get 10.10 back up and running later. I am also begrudgingly looking at rsavage's 7 page thread for some answers too. :P

Thanks,
MP

---

### Post by pauljwells on 2011-11-09
Yep, this is pretty much all there is to it until you start hacking the source yourself. I know rsavage and you haven't really seen eye to eye ;-) but he posts very useful stuff and there really aren't many active ppc users out there. I sometimes wonder if it would be better to forget ubuntu and go with linuxopjemac's mintppc - if we all used just one distro we'd be able to pool resources, even though I personally really like unity-2d!! 
I do sympathize with your view about installing >10.10 - it really isn't straightforward. I have a shaky install of 11.04 from when it was available on the daily builds as a beta, but I know there is no install image of 11.04 available now :-(
If ever I get 11.10 or later to install I'll post full details.
I have a separate HD in my G5 for ubuntu so I never have to worry about the OSX installation. Highly recommended as it just slots in to the bay.

---

### Post by MacPenguin1972 on 2011-11-09
> **pauljwells said:**
> Yep, this is pretty much all there is to it until you start hacking the source yourself. I know rsavage and you haven't really seen eye to eye ;-) but he posts very useful stuff and there really aren't many active ppc users out there. I sometimes wonder if it would be better to forget ubuntu and go with linuxopjemac's mintppc - if we all used just one distro we'd be able to pool resources, even though I personally really like unity-2d!! 
I do sympathize with your view about installing >10.10 - it really isn't straightforward. I have a shaky install of 11.04 from when it was available on the daily builds as a beta, but I know there is no install image of 11.04 available now :-(
If ever I get 11.10 or later to install I'll post full details.
I have a separate HD in my G5 for ubuntu so I never have to worry about the OSX installation. Highly recommended as it just slots in to the bay.


I agree. In fact to me Linux should be the system of those who don't want to cow-tow to the demands of the big corporate PC makers to begin with.  I figure the computer "rebel" would still want to use the Power PC since it flies in the face of the big corporations! lol!

But yeah, back to 10.10 for me. "Last known good configurarion". to use a quote. lol! (That's an actual Microsoft joke of course, on Windows there is no such thing! haha!)

The Power PCs are still viable machines - I use Mac OS X 10.4.11 Tiger on my G5 and I'm amazed at what I can still do on this thing.  I may find me a copy of Mac OS X 10.5 to use when I feel like paying someone on eBay $100 for a copy of it.  But yeah, I've been wanting to run a dual platform machine with OS X and Linux.

I do eventually want to have a second Linux version. I am looking at Mint but it's confusing. It's like you have to load Debian first THEN put Mint - he said on his website he won't make an iso disc file but I wish he would. Would be easier to just pop in a disc and load it.  (I'm oldschool on stuff like that. lol!)

I agree- there is a need for more unity among PPC users. I was kind of hoping Ubuntu would take that direction but I'm having my doubts.  I even tried 12.04 (there are PPC iso files for that but it's the same errors as 11.10. So I think until we can overcome the 11.10 hurdle...  "crawl first, then walk?"

(off topic comments removed by MacPenguin1972)

But you've been a lot more helpful on providing "how to" information, so I appreciate it. That has been what I have been looking for all along.

I just wish the Apple Forum would be split into "Power PC" and "Mactel" subforums to separate the two camps, as they should be just for the sake of simplicity since things for Mactel will not work for PowerPC and vise versa. 

Anyhoo.. yeah, thanks again. I'll have to mess with this a bit more.

:D
MP

---

### Post by rsavage on 2011-11-09
> **MacPenguin1972 said:**
>   But that guy seems to want to pimp everyone to rely on THAT thread for "all your Ubuntu needs".  He simply shoots down everything I say without any supporting facts to back up his arguments, that's my biggest beef with him. That and his constantly playing at being "naive" about what I'm after, and after I've clearly spelled it out several times.

Whatever.  Go figure it out yourself.

---

### Post by MacPenguin1972 on 2011-11-09
> **rsavage said:**
> Whatever.  Go figure it out yourself.

Your true attitude finally comes out.

---

### Post by nothingspecial on 2011-11-09
As this has descended into an argument....

Closed.

---

### Post by Elfy on 2011-11-09
Re-opened - keep this ontopic or will be closed again.

---

### Post by MacPenguin1972 on 2011-11-09
> **forestpiskie said:**
> Re-opened - keep this ontopic or will be closed again.

No problem. My apologies about the situation. I have also removed the off topic comments from my last post.



**@ nothingspecial** --* "Linux assumes you know exactly what you are doing " *

man, you ain't kidding about THAT! lol! 

Peace! :-)

---

### Post by MacPenguin1972 on 2011-11-09
I think to add to this compiling idea. I'm going to reinstall Ubuntu 10.10 and see if I can upgrade it from inside Linux that way and mess with compiling some programs. Should work for anything with a source code right?

Before I do any upgrading I think I'll try that first- see if I can do "SeaMonkey" just for kicks and go from there.

---

### Post by canhoto on 2011-11-09
Well, after 30 hours of building, I finally had all the libreoffice deb's created in the building directory. Then, the question: where to dtart?

I began trying to install by double-clicking (which launches GDebi installer). Each time there was a dependency error message. I followed the path it pointed to, trying to install the dependencies. I finally got stuck, when, after trying to install ure_1.7.0+LibO3.3.2-1ubuntu2~maverick1_powerpc

I got this message
> Dependency is not satisfiable: uno-libs3 (= 1.7.0+LibO3.3.2-1ubuntu2~maverick1)

I then tried to install the uno-libs3_1.7.0+LibO3.3.2-1ubuntu2~maverick1_powerpc
and I got this message:
> Breaks existing package 'ure' dependency uno-libs3 (= 1.6.1+OOo3.2.1-7ubuntu1.1)

What should I do? Give up Libreoffice (which I like better than OpenOffice)?

I'm affraid to try the same with Firefox (wait for a whole day to have the builds and then not being able to install it because of the dependencies)

---

### Post by rsavage on 2011-11-09
Canhoto, I knew you'd be posting back on here!  That is why I got this thread reopened! You need to upgrade the ure package to 1.7.0 too.

---

### Post by rsavage on 2011-11-09
The best thing to do is to get synaptic to know about all the updated packages.  If you look in the File menu there is an option to 'Add downloaded packages'.  I don't know if that is the best option to do it.  Pauljwells has more experience at this than me probably and he may know.  When synaptic knows where everything is you can then tell it to install libreoffice.  It should sort everyting out itself.  You may also have to uninstall Open Office if it uses the same packages and is insisting on old versions.

---

### Post by canhoto on 2011-11-09
Thanks
> **rsavage said:**
> Canhoto, I knew you'd be posting back on here!  That is why I got this thread reopened! You need to upgrade the ure package to 1.7.0 too.

Sure, but if I try to install it right from the deb, it will tell me:
> Dependency is not satisfiable: uno-libs3 (= 1.7.0+LibO3.3.2-1ubuntu2~maverick1)I tried to upgrade it with Synaptic, forcing the version, but that version doesn't appear (as if my version was the most recent).

I also tried to remove it from within Synaptic, so that I could install the new version, but it would uninstall all the Openoffice packages (which I don't want to)

---

### Post by canhoto on 2011-11-09
> **rsavage said:**
> The bestried thing to do is to get synaptic to know about all the updated packages.  If you look in the File menu there is an option to 'Add downloaded packages'. 

I did that, choosing the libreoffice-build directory where they are, but they don't appear in any list (neither "local", nor "all")

---

### Post by rsavage on 2011-11-09
Okay, looking into it I don't think the 'Add downloaded packages' is the correct thing to use.  Sorry about that.

Have you tried
```
sudo dpkg -i ./*.deb
``` 
as suggested at the end of pauljwells instructions?

---

### Post by canhoto on 2011-11-09
> **rsavage said:**
> Okay, looking into it I don't think the 'Add downloaded packages' is the correct thing to use.  Sorry about that.

Have you tried
```
sudo dpkg -i ./*.deb
```as suggested at the end of pauljwells instructions?

Yes, sure, that was it, it was so simple! I thought you had to replace * by the name of the package, and not just run the command.

Well, it installed, but I still have a problem:

- The list of programs (writer, calc, draw, impress, etc.) appears in my office applications submenu. But without icons. And when I choose it, nothing happens. I tried to run it from within terminal, but with no success.
Opening Synaptic, I get the message saying that I have 21 (I think) broken packages. I filtered it and... it was the libreoffice packages. I choosed to "fix the broken packages", but after some seconds all the packages got the orange "x", meaning that they would be removed... I did nothing of course. But now I have it apparently installed, but not working, and with this broken packages stuff.

I also feel that the computer is using more CPU than before (I felt that before after "installing" it, but after building). But I'm not sure, it gets to 100% when I open a webpage or an application, than it falls down. Maybe it's just normal.

Any suggestion?

---

### Post by canhoto on 2011-11-09
> **canhoto said:**
> 

Well, it installed, but I still have a problem:

- The list of programs (writer, calc, draw, impress, etc.) appears in my office applications submenu. But without icons. And when I choose it, nothing happens. I tried to run it from within terminal, but with no success.
Opening Synaptic, I get the message saying that I have 21 (I think) broken packages. I filtered it and... it was the libreoffice packages. I choosed to "fix the broken packages", but after some seconds all the packages got the orange "x", meaning that they would be removed... I did nothing of course. But now I have it apparently installed, but not working, and with this broken packages stuff.

I also feel that the computer is using more CPU than before (I felt that before after "installing" it, but after building). But I'm not sure, it gets to 100% when I open a webpage or an application, than it falls down. Maybe it's just normal.

Any suggestion?

SUCCESS! I just let it go with the broken packages fixing. I had to so that I would be able to do the same with Firefox 7 (it asked for that when running the dependencies command).
Suddenly, I discovered that OpenOffice was no longer there. When fixing the broken packages, it removed OpenOffice. I then reinstalled  LibreOffice again with the command that our good friend suggested. And... voilá! It's fully working (and it's more up-to-date and clean than the Openoffice I had). So, to install LibreOffice, you have to remove OpenOffice.org.

No problem!

Maybe I will tell this LibreOffice process on a new thread, maybe it will be helpful to someone.

Thanks!

---

### Post by canhoto on 2011-11-13
> **pauljwells said:**
> Usually you get the error you are seeing because there is no ppc version of the library available in any repo, so you have to build it yourself. Just create a new build directory and run through the process for the dependency first and then you can go back to the main Firefox build.

You should be able to download the source for the dependency directly with ```
apt-get source foo
``` without needing a ppa version.

Any idea of how this could work with Dropbox?

---

