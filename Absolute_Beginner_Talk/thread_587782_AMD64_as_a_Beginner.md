---
title: "AMD64 as a Beginner?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Vekin on 2007-10-23
I was just wondering if switching to AMD64 for 7.10 is a good idea?  I know some of the basics, but most of the command line stuff eludes me, so I'm afraid I'm gonna run into problems, like the one I've heard about flash, for example, and have a hard time fixing them.

Also on that note, is there a place where I can just go and learn some of the basics about the console, like how to navigate, install files, and some basic commands?  It seems right now all the info that I can find is very specific to certain actions or scattered about.

---

### Post by dfreer on 2007-10-23
Flash is working great for me in gutsy amd64, and it's rather easy to install (I use the non-free plugin, not gnash btw).

---

### Post by Soarer on 2007-10-23
I don't think the 64bit version is any harder to run or use than the 32bit one, but as always YMMV.

Flash is OK using the nonfree plugin as stated, but the Java plugin in Firefox is a problem.

---

### Post by FredB on 2007-10-23
> **Soarer said:**
> I don't think the 64bit version is any harder to run or use than the 32bit one, but as always YMMV.

Flash is OK using the nonfree plugin as stated, but the Java plugin in Firefox is a problem.

It is not anymore, if you want.

You can install Iced Tea from Doko repository (an ubuntu coder) which have a working java plugin.

Just add this to your /etc/apt/sources.list :

```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/  gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```

Hope it helps ;)

---

### Post by realvz on 2007-10-23
i still dont think its right time togo 64bit....the software support sucks in 64bit...

---

### Post by misfitpierce on 2007-10-23
Only place 64 bit can get tricky is trying to run 32 bit programs... Sometimes a headache but there is not much need for having to force 32 bit as most programs come 64 bit as well now. :)

---

### Post by misfitpierce on 2007-10-23
> **realvz said:**
> i still dont think its right time togo 64bit....the software support sucks in 64bit...

Very false and thats one reason 64 bit will never keep continuing to grow b/c of ppl spreading false statements. Over 90% of programs made 32 bit are 64 bit as well. Can even run 32 bit if so compelled. :)

---

### Post by realvz on 2007-10-23
> **misfitpierce said:**
> Very false and thats one reason 64 bit will never keep continuing to grow b/c of ppl spreading false statements. Over 90% of programs made 32 bit are 64 bit as well. Can even run 32 bit if so compelled. :)

You maybe right...i didnt give it enough time either..

just a thought...does it really make that much difference when u are on 64bit OS with 32bit apps running...

---

### Post by Soarer on 2007-10-23
> **FredB said:**
> It is not anymore, if you want.

You can install Iced Tea from Doko repository (an ubuntu coder) which have a working java plugin.

Just add this to your /etc/apt/sources.list :

```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/  gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```

Hope it helps ;)

Looks good. I've added the repos, uninstalled Blackdown 1.4 and installed iced Tea but about: plugins now doesn't report any Java plugins loaded. The Sun Java plugin verification doesn't run.

Is there some more config I need to do?

Thanks.

---

### Post by barkej on 2007-10-23
> **realvz said:**
> You maybe right...i didnt give it enough time either..

just a thought...does it really make that much difference when u are on 64bit OS with 32bit apps running...

Not really when you are running 32-bit apps. I will say that i have not found any need to install a 32-bit app since going back to a 64-bit install.

---

### Post by FredB on 2007-10-23
> **realvz said:**
> i still dont think its right time togo 64bit....the software support sucks in 64bit...

Can you have some examples ? Or is it somply because you've heard that ?

Windows 64 bits software sucks and it is the truth. But not for linux 64 bits...

---

### Post by FredB on 2007-10-23
> **Soarer said:**
> Looks good. I've added the repos, uninstalled Blackdown 1.4 and installed iced Tea but about: plugins now doesn't report any Java plugins loaded. The Sun Java plugin verification doesn't run.

Is there some more config I need to do?

Thanks.

Did you install iced tea plugin -> icedtea-java7-plugin package ?

---

### Post by FredB on 2007-10-23
> **barkej said:**
> Not really when you are running 32-bit apps. I will say that i have not found any need to install a 32-bit app since going back to a 64-bit install.

The only 32 bits program I have on my Gutsy ? Flash plugin because gnash sucks too much right now.

---

### Post by AngelBreath on 2007-10-23
You can do it this way: Install 32bit Ubuntu-->install VMware server--> try 64bit Ubuntu in a virual pc , check applications and if everything is ok you go to 64bit as your basic installation. 
 Actually i use this way for every test in my pc's and even if it sounds a little "?" i have the same installation in my pc for almost 2 years with not even 1 crash....:):)

---

### Post by Soarer on 2007-10-23
> **FredB said:**
> Did you install iced tea plugin -> icedtea-java7-plugin package ?

Yes - got it working after a while. I looked in the README (shock!) and found I needed to update the Java-alternatives. Restarted Firefox & it now reports Java 1.7 as working.

Thanks for your help - this was the only little niggle I had with Gutsy 64bit. :)

---

### Post by dfreer on 2007-10-23
> **AngelBreath said:**
> You can do it this way: Install 32bit Ubuntu-->install VMware server--> try 64bit Ubuntu in a virual pc , check applications and if everything is ok you go to 64bit as your basic installation. 
 Actually i use this way for every test in my pc's and even if it sounds a little "?" i have the same installation in my pc for almost 2 years with not even 1 crash....:):)

I didn't know you could run 64-bit clients from a 32-bit host, that's good to know.

---

### Post by evilregis on 2007-10-23
I installed AMD64 on a computer for my dad but reinstalled an i386 version of Ubuntu because he wants Skype and it's an i386 package.  I've since read that you can make it work... I don't know how involved the process is though.

And I forget what exactly was the hangup on my wife's computer, but on hers too I ran into a snag (a driver, I believe) that was only 32-bit and would get an error trying to install it.  So I moved her back to i386.

I'm nowhere near being competent in Linux so I wasn't about to start going crazy trying to get those to work when I can just install a different version and have the new OS up and running with the software installed in the amount of time it'd probably have taken me to figure out the 64bit problem.

---

### Post by misfitpierce on 2007-10-23
> **realvz said:**
> You maybe right...i didnt give it enough time either..

just a thought...does it really make that much difference when u are on 64bit OS with 32bit apps running...

No it would not make a difference to 32 bit app's as they are locked on how they are made for 32 bit. 64 bit programs and file moving etc will show much improved speed though.

---

### Post by misfitpierce on 2007-10-23
Also the comment about the 32 bit skype. There is a way to do it and you can google for it. There was a guide somewhere. 64 bit automatix installs skype without a hitch as well. Not turning this into automatix frenzy so dont comment on the program just stating...

---

### Post by dfreer on 2007-10-23
I know I had 32-bit skype working back on edgy or feisty. I wrote a how-to on ubuntuguide.org, it may still be relevent. Since I haven't used it in forever, there may be an even easier way as well.

---

### Post by smaller on 2007-10-23
> **Soarer said:**
> Yes - got it working after a while. I looked in the README (shock!) and found I needed to update the Java-alternatives. Restarted Firefox & it now reports Java 1.7 as working.

Soarer, I'm experience the same problem as you, can't get java to work in firefox on Gutsy 64 bit. Like you I have also got the icedtea plugin (openjdk 7) installed, but it still isn't working. Which README file are you referring to? I can only find 2 README files under /usr/lib/jvm/java-7-icedtea/ and both are pretty useless, for the purpose of installation problems at least. :-)

I'd also like to know what you mean by update the java-alternatives... are you talking about synaptic package? If so I can't seem to find it. Or do you mean that /etc/alternatives/java has to be a symbolic link to the icedtea java script? Because that already seems to be the case on my system but to no avail. 

> **Soarer said:**
> Thanks for your help - this was the only little niggle I had with Gutsy 64bit. :)

Same here, running really smooth other then this. However, I consider this more then just a little niggle because this is my only PC/OS so due to this bug I'm currently unable to access internetbanking.. :(

---

### Post by Vekin on 2007-10-23
Well, here are my stats:

AMD Athlon 64 X2 Dual Core Processor 4200+ 2.21 GHz
2 GB of RAM
GeForce 7600 GT

I'm planning to try to install it on an external harddrive and just run it from that, while formating my computer for Windows XP so I can run the programs for my homework and such.  That, and a portable computer would be nice =D.  I don't do much video or image editing, and I'm gonna try to get Steam to run on Ubuntu so I can play my games on there.  Do you think I would see a great enough benefit from AMD64 to warrent switching?  Remember, I'm very newbish with Ubuntu, so problems you guys may find minor, I will have a bit of trouble with.

---

### Post by Soarer on 2007-10-24
> **smaller said:**
> Soarer, I'm experience the same problem as you, can't get java to work in firefox on Gutsy 64 bit. Like you I have also got the icedtea plugin (openjdk 7) installed, but it still isn't working. Which README file are you referring to? I can only find 2 README files under /usr/lib/jvm/java-7-icedtea/ and both are pretty useless, for the purpose of installation problems at least. :-)

I'd also like to know what you mean by update the java-alternatives... are you talking about synaptic package? If so I can't seem to find it. Or do you mean that /etc/alternatives/java has to be a symbolic link to the icedtea java script? Because that already seems to be the case on my system but to no avail. 


Hi Smaller - just woke up. Sorry for the delay. :)

I looked in /usr/share/doc/icedtea-java7-jre/README.alternatives. To save you the trouble, it says:

> Starting with java-common 0.23ubuntu1, the update-java-alternatives
script can be used to set a bunch of jre/jdk alternatives:

- Set all runtime tools to point to the icedtea-java7 alternatives:

  update-java-alternatives --set --jre icedtea


- Set all runtime and development tools to point to the icedtea-java7
  alternatives:

  update-java-alternatives --set icedtea


- Set all runtime and development tools to auto mode:

  update-java-alternatives --auto

So I did that (a;though you have to put 'icedtea-java7' where it has icedtea IIRC) and restarted FF and it worked. Look in about : plugins in FF to see the Java being used, or go to the Sun Java test site ([http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)). 

I believe sometimes different Java versions can conflict, so I removed the Blackdown Java I was using before, but Sun Java 6 is still on the system. Icedtea is the default, though.

---

