---
title: "is someone hacking my laptop?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by riminicat on 2007-12-06
I didn't know where this question should go so I put it here.  An official from my school came to me today and told me some one has been hacking into the servers and taking peoples personal data.  I'm not sure how they would do that but he mentioned Java Script.  Any way they blamed me and gave me a bunch of crap about the FBI and stuff.  Wanting to show that I was innocent I gave them my laptop, booted into Ubuntu and let them check for programs that could be used to hack.  They went to a website and then went into another room to check something, probably another computer to see if I showed up.  They came back and said something about keys matching, keys that are specific to Mozilla Firefox and that all versions of Ubuntu 7.10 has.  They said the problem with this is that the computer showed who ever is hacking is hacking from France, which I know some one could make it look like that without actually being in France.  Any way, is there a way I can tell if someone got into my laptop somehow, even remotely?  I don't believe the schools crap about the FBI and I obviously don't live in France.  Thanks for any help.

---

### Post by wolfen69 on 2007-12-06
install a firewall such as firestarter, and check the events log.

---

### Post by LaRoza on 2007-12-06
This sounds fishy.

If you are using Linux, it is unlikely anthing is running on your computer, and it looks like the "hacker" is just a way to invade personal space.

It is probably a student of that school. JavaScript is a client side scripting language.

If you are not doing anything to breach security, there is no reason to be alarmed. 

As for the Firefox thing, Firefox and Opera can be masked as other browsers, so using a program to determine what browser is being used is impossible to state accurately. 

Don't relinquish your personal belongings anymore, and ask if your student data is compromised, and if it is, have it secured.

As a student, you are a customer of this school, make sure your information is secured.

---

### Post by bodhi.zazen on 2007-12-06
Well, limiting the discussion to what to do if you have been compromised ...

1. disconnect from the internet.

2. image the hard drive for forensics.

3. Wipe hard drive and re-install. Choose a stronger password and see this link re: browser security :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by thelatinist on 2007-12-06
So basically if I understand this correctly, they are suggesting that you are smart enough to  cover your tracks using a proxy and to hack into the school database using...a web browser and Java script, but that you aren't smart enough to forge your useragent?

---

### Post by riven0 on 2007-12-06
Sounds like a bunch of garbage to me. If they really thought you were hacking into their system, where is their warrant? Besides that, where is their proof? They go to another room and, (apparently), check something up and then come back and tell you the numbers match?! Something sounds fishy. I wouldn't be handing over my laptops to anyone if I were you. 

I don't want to sound paranoid, but if I were you I would wipe out Ubuntu and re-install. There is no telling what they put on your laptop now.

---

### Post by rsambuca on 2007-12-06
This is some brave form of fraud.  Did you get to see any ID from these 'officials'?  Wipe your drive, change any passwords that may have been compromised, and report the incident to the Dean.

---

### Post by antisocialist on 2007-12-06
chances are these "officials" have no idea how to make a program for linux, but it is still worth wiping ur computer and reinstalling ubuntu just in case.  also, be sure to report this to the dean, and dont hand your laptop out like halloween candy unless they have a warrant.

---

### Post by FuturePilot on 2007-12-06
That definitely sounds fishy. I would image the hard drive so you can pick it apart later, and then reinstall. And change any passwords that might have been compromised. You should demand proof on why they targeted you as the suspect. It doesn't seem to make sense.

---

### Post by stchman on 2007-12-06
> **riminicat said:**
> I didn't know where this question should go so I put it here.  An official from my school came to me today and told me some one has been hacking into the servers and taking peoples personal data.  I'm not sure how they would do that but he mentioned Java Script.  Any way they blamed me and gave me a bunch of crap about the FBI and stuff.  Wanting to show that I was innocent I gave them my laptop, booted into Ubuntu and let them check for programs that could be used to hack.  They went to a website and then went into another room to check something, probably another computer to see if I showed up.  They came back and said something about keys matching, keys that are specific to Mozilla Firefox and that all versions of Ubuntu 7.10 has.  They said the problem with this is that the computer showed who ever is hacking is hacking from France, which I know some one could make it look like that without actually being in France.  Any way, is there a way I can tell if someone got into my laptop somehow, even remotely?  I don't believe the schools crap about the FBI and I obviously don't live in France.  Thanks for any help.

Sounds like a load of BS.  So they think that you are the only person that uses Firefox on that campus?

---

### Post by hyper_ch on 2007-12-06
> **wolfen69 said:**
> install a firewall such as firestarter, and check the events log.

Firestarter is NOT a firewall but merely a frontent for iptables.

And upon reinstalling your stuff, I'd also encrypt the whole thing ;) If you get the alternate install CD it provides an option for you to do that (however it is then recommended that you make backups on a regular base to some other device as everything will be encrypted and if anything goes wrong you can't really access it anymore...)

---

### Post by riminicat on 2007-12-06
Hey guys thanks for all the help and the posts.  I looked into the people checking my laptop and they were people that work for my university's IT apartment.  I'm also checking my terminal to find out what commands they ran and if they compromised any thing I'll have it dealt with.  Man, this is like something out of a movie.  Thanks for all your help.

---

### Post by riminicat on 2007-12-06
Ok, I checked to see what commands they ran on my laptop and they must not be very smart.  But here they are:




apt-get -V
pwd
yum
tree
ls -R
ls /usr/local/bin/
ls /root
ls /opt
ls /opt/Planeshift/

---

### Post by Swmmrman on 2007-12-06
Total load of bull IMO.  I agree with the others.  Reimage reinstall.  Never know if they have some stuff they downloaded.

---

### Post by LowSky on 2007-12-06
Why did you even let them touch your stuff? Dude learn your rights as an American.

Please tell me you didn't give them your passowrds.

---

### Post by riminicat on 2007-12-06
I didn't give them my passwords, I didn't let them touch anything at all.  I am done going to this school so I have to turn my laptop back in(its school issued) So I'm going to reimage and write over the hard drive as many times as I possibly can first, I have all the data I need in another location that know one knows of.  I also told them I will be calling a lawyer if they continue the matter further.

---

### Post by rsambuca on 2007-12-06
Hey, you never told us it was your school's computer!  Read your agreement, it probably has a clause whereby they are entitled to check it.

---

### Post by riminicat on 2007-12-06
> **rsambuca said:**
> Hey, you never told us it was your school's computer!  Read your agreement, it probably has a clause whereby they are entitled to check it.

My bad, they can check it.  But I still wonder what they were doing and why they thought it was me.  Oh well, as long as they don't keep pursuing it I'm over it.  Thanks for your help guys.

---

