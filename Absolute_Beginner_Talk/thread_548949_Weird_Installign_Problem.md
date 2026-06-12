---
title: "Weird Installign Problem"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by mari0- on 2007-09-11
Well I spent most my day trying to install MadWifi on my laptop. I was getting this weird error though. My friend was attempting to help me we were going good then shot down by this have a look.

```
mari0@usuck:~$ sudo apt-get install build-essential
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
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

Then, after trying to install libc6-dev and g++ they would not install.

```
mari0@usuck:~$ sudo apt-get install libc-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libc6-dev instead of libc-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.5-0ubuntu14) but 2.6.1-2 is to be installed
E: Broken packages

```

Any ideas to get libc and g++ installed so I can get this working. I get the errors when tryign to download the build essentials package

---

### Post by mostwanted on 2007-09-12
Note the E: Broken packages error message at the bottom of your text output!

Synaptic has a filter that allows you to locate broken packages. Remove those packages and start over. Apt-get is a very basic install tool, I don't recommend using it. Aptitude is better if you prefer the command line.

---

### Post by ravenwere on 2007-09-12
When did you last update your packages. The error seems to indicate your libc6 file (which is required in ubuntu) is of an earlier version than the libc6-dev which you are trying to install.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If this is the problem your libc6 will be updated and you should then be able to install libc6-dev.

---

### Post by Lex_x64 on 2007-09-17
I appear to be getting the same problem as mari0-. I've tried installing the lib6c using synaptic only for it to give the same depends (and ver.) error. 

I tried the update and upgrade commands you suggested ravenwere but ran into this:

```
Compy@lex-desktop:~# **sudo apt-get update**
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 0s (3B/s)
Reading package lists... Done
```

```
Compy@lex-desktop:~# **sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
**_0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded._**
```

So the libc6 and libc6-dev are still at different versions. Are there any other ideas out there?

---

### Post by ravenwere on 2007-09-17
Broken packages error message? Mostwanted's point is well made. If you are using synaptic check for any broken packages.

Step 1.
You can also verify with Synaptic what versions of libc6 are installed or available from your repositories. You seem to have all the main repositories included in your sources list.

You can also check this with ```
apt-cache show libc6
```or whatever package you are interested in.
(Out of interest my version of libc6 is only 2.6.1-1ubuntu4 not 2.6.1-2 as in the error message)

Step 2
Broken packages can be dealt with by```
sudo apt-get install -f
```.

Step 3
Failing the above I personally would remove the relevant packages and reinstall them. 
```
sudo apt-get remove libc6
```
```
sudo apt-get install libc6
```

It doesn't apply with the lib files but in the case of removing a regular package I would also purge the configuration files
```
sudo apt-get remove --purge *package name*
```
then
```
sudo apt-get install *package name*
```
or more simply
```
sudo aptitude reinstall --purge *package name* 
```

If you get any relevant error messages please post.

---

### Post by Lex_x64 on 2007-09-18
Uh, well to be honest; I hosed the system after removing the libc6 package (I had a feeling I would). So I pulled the Microsoft answer of format and reinstall. Everything is working quite well now.

Just to clarify a few things as well: When I opened Synaptic, there were no broken packages, the version for libc6 was 2.6.1-1 but the rest were 2.5.x-x, and telling Synaptic to "fix the broken packages" didn't do squat.

Unfortunately that leaves no real "easy" help to fix mari0-'s problem if they are still having it heh.

---

### Post by ravenwere on 2007-09-18
Hi Lex,

Did you mean your system broke after reinstalling libc6? 'cause I just did the same reinstall while typing this and burning a cd and there has been no problems at all. It is a required package though,

One thing I did need to check as well. I notice there is a package now for libc6-amd64 and I'm  wondering whether that is causing some confusion in the package database (I am assuming you have a 64bit system from your online name). Did you install the 64bit version of Ubuntu?

Other than that any other ideas - greatly appreciated.

---

### Post by Lex_x64 on 2007-09-18
I more then likely didn't go about it the proper way. I should have just done it with Synaptic; but instead I went to the prompt and killed x. After no success just reinstalling the package (starting X again and nothing being different) I returned to the terminal, removed libc6 even though I knew it would remove the apt command with it. Then, up the creek without the knowledge (or bootable system) no knowing how to install the package I started fresh.

Your correct to assume I'm using the 64-bit version. I took a screenie of the package list and sent you an IM with it attached. (I didn't want to scale it down too much to fit the .jpg LxW requirements).

---

### Post by ravenwere on 2007-09-18
Thanks for the feedback Lex,

To tidy this thread up - there appears to be a circular dependency in the feisty repository involving the packages g++-4.1 and libstdc++6-41-dev

The alternative is to download the gcc-4.1 package (thanks rajan)  which contains the g++ (c++) compiler.

[http://ubuntuforums.org/showthread.php?p=3383172#post3383172](http://ubuntuforums.org/showthread.php?p=3383172#post3383172)

---

