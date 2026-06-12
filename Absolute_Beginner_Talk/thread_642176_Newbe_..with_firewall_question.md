---
title: "Newbe ..with firewall question"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by pepper* on 2007-12-16
Hi Guys 
im new here .. to Ubuntu and the forum ..
this Forum and the operating system is GREAT ..

im having trouble installing a firewall ( firestarter )
i tried what it says .. go to system then administration then to software sources 
and then third party ,to add " Universe" but it wont accept anything i type in ..

sorry abut the question if it's stupid ..
but you havt to remember i was a window user ..

thanks for the help in advance ..........  Jim

:):):):):):):):)

---

### Post by timbounceback on 2007-12-16
hmmm.... have you tried following the steps here: [http://www.howtoadvice.com/FirestarterInstall/](http://www.howtoadvice.com/FirestarterInstall/)

---

### Post by ocirs on 2007-12-16
Just make sure you check off the first four check boxes under the ubuntu software tab. Then go to system-> administration -> synaptic software manager and hit the blue reload on top to download all the new source list. Then click search and type in firestarter and it should be listed in the results. Just check the box select mark for installation click apply and you should be all set!

---

### Post by Malta paul on 2007-12-16
Hi, Welcome,
You can install Firestarter by going to Applications>Add/remove  Tick Show 'all available applications' Then in the search box type Firestarter. when found Apply changes.
Firestarter can then be found in System>Administration.   You will need root privileges to start (your root password) 
Hope this helps you:)

---

### Post by pepper* on 2007-12-16
THANKS GUYS    .

i did what you said , and now firestarter is up and running..

Does Ubuntu / Linux need a firewall ??

:guitar::guitar::):):):):guitar::guitar:

---

### Post by thelatinist on 2007-12-16
> **pepper* said:**
> THANKS GUYS    .

i did what you said , and now firestarter is up and running..

Does Ubuntu / Linux need a firewall ??

:guitar::guitar::):):):):guitar::guitar:

Firestarter is NOT a firewall.  Linux has a built in firewall called iptables, and the default settings should be fine for most desktop users.  If you have a static ip address or have installed software such as server application that will be listening for incoming connections, you might want to close ports and leave open only what you want.  That's where Firestarter comes in.

Firestarter is merely a GUI that allows you easily to configure iptables. It has a wizard for making initial settings and makes it easy to add custom rules.  It is still not your firewall, iptables is.  Once you have made your settings in firestarter, you can close it.  iptables will continue to run in the background and keep your computer safe.

Since most people who ask this question also are looking for antivirus software, too, let me add that antivirus software is completely unnecessary in Linux unless you are running it as a mail server.  Don't bother looking.

---

### Post by seventhc on 2007-12-16
> **thelatinist said:**
> Firestarter is NOT a firewall.  Linux has a built in firewall called iptables, and the default settings should be fine for most desktop users.  If you have a static ip address or have installed software such as server application that will be listening for incoming connections, you might want to close ports and leave open only what you want.  That's where Firestarter comes in.

Firestarter is merely a GUI that allows you easily to configure iptables. It has a wizard for making initial settings and makes it easy to add custom rules.  It is still not your firewall, iptables is.  Once you have made your settings in firestarter, you can close it.  iptables will continue to run in the background and keep your computer safe.

Since most people who ask this question also are looking for antivirus software, too, let me add that antivirus software is completely unnecessary in Linux unless you are running it as a mail server.  Don't bother looking.

Firestarters definition under add/remove:
Firestarter is a complete firewall tool for Linux machines. It features an easy to use firewall wizard to quickly create a firewall. Using the program you can then open and close ports with a few clicks, or stealth your machine giving access only to a select few. The real-time hit monitor shows attackers probing your machine.

and my opinion on av:
AV software is good for people who trade files between different windows users.I'd like to know it's not infected before I send it to a friend if I'm going to share it. saying you dont need it is your opinion don't state it as fact.

---

### Post by thelatinist on 2007-12-16
> **seventhc said:**
> Firestarters definition under add/remove:
Firestarter is a complete firewall tool for Linux machines. It features an easy to use firewall wizard to quickly create a firewall. Using the program you can then open and close ports with a few clicks, or stealth your machine giving access only to a select few. The real-time hit monitor shows attackers probing your machine.

and my opinion on av:
AV software is good for people who trade files between different windows users. saying you dont need it is your opinion don't state it as fact.

It is a firewall *tool* and a firewall *wizard* used to configure the firewall already built into linux.  It is not a firewall.

Let me rephrase: antivirus software is absolutely *not* necessary if you follow basic computing safety guidelines.  If you're foolish enough to pass executables of unknown origin on to your windows friends (why would you even have such files on your system anyway?), then by all means bloat your system with useless antivirus software.  Otherwise, don't worry:  your windows-using friends' viruses won't touch your computer, so there's really nothing to worry about.  Not opinion, fact.

---

### Post by seventhc on 2007-12-16
ummm...I think anti virus software is basic computing safety.
I don't dl exe's I just mean like if one friend forwards me a funny pic or whatever and I want to share it with someone I would feel very incompetent if it had something embedded in it and hosed there windows. I know they are responsible for themselves but at the same time I don't want to infect my friends. I know it probably would never happen as I don't forward things to much but anything is possible. Better safe than sorry
but now we are getting off topic. so let this end.

a quote from [http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)

[FONT=Arial,Helvetica][SIZE=3]**Keith Peer:** Currently there are under 100 native Linux viruses known but in many organizations the fact that a Linux viruses exists is enough reason to install and use Linux antivirus protection on Linux desktops and servers. Additionaly users of StarOffice and OpenOffice.org have the ability to open and view Microsoft Office documents that may contain viruses. These viruses may not infect the Linux computer but the user can easily attach and send these infected documents unknowingly to someone else and that is a serious problem.[/SIZE][/FONT]

---

### Post by thelatinist on 2007-12-16
Basic computing safety is not opening forwarded attachments from unknown sources, no matter how "funny" they supposedly are.  It means not perpetuating such resource-wasting and dangerous forwarded messages.   And It means not enabling macros you don't understand and whose source you know.  You are using antivirus software as a crutch for carelessness and lax security.

---

### Post by seventhc on 2007-12-16
I am not talking about unknown sources, sometimes information must be shared to achieve certain goals. I used a bad example but this is my last post on the subject.
I use AV as an added precaution to enhance my overall security. 
I'm not sure how taking extra measures makes me careless but somehow in your twisted little world it does.

end of discussion.

---

### Post by discoade on 2007-12-16
thelatinist......   some people just don't get it do they! if they wish to pass dodgy files between them selves then let them get on with it i say! but im with you on this one!

---

### Post by seventhc on 2007-12-16
Nope you misunderstand. I don't pass along dodgy files since I know they are not infected and I don't go forwarding useless info. But really these are all our separate opinions and it really doesn't need to turn into a battle. You don't run  AV software and thats fine, I choose to run it and that should also be fine. I also use WPA over WEP since I know WEP is easily compromised.
It's my box and I'll do what I want ;)
But please no more bickering. I'm here to get help and to help when I can.

---

### Post by discoade on 2007-12-16
well my apologies sir! as i say i don't deem AV as necessary but having said that i do know someone who wants it so perhaps you could recommend one to me? its not a subject i have ever looked into! and knowing her it will have to be free! :)

---

### Post by HDave on 2007-12-17
You do not need virus protection on Linux.  It has nothing to do with the fact there are fewer viruses for Linux, it has to do with the fact that Linux has many fewer attack vectors for malware of all kinds -- not the least of which is you are NOT running as root.

Read this:

[http://www.linux.com/articles/60208]("http://www.linux.com/articles/60208")

So skip firestarter and skip anti-virus...not needed here...

---

### Post by seventhc on 2007-12-17
I use ClamAV , it's good for people who are transferring documents between different machines. It isn't there to protect my Linux, it is there to ensure that whomever gets it after me is safe. These are documents that have to be traded for work purposes so I use the added precaution. :)

---

### Post by hyper_ch on 2007-12-17
why should I waste my computer power so that others feel safer? it's up to them to make themselves safe... if they want to use windows then it's their choice but they also ahve to deal with the consequences of that choice...

And once they need to resetup their machines again you can just say: "Oh, you got another virus? I haven't had issues with them ever since I switched to linux... nothing's hogging my system down anymore"

---

### Post by High Camp on 2007-12-17
What a completely useless topic. If you read the original post the poor guy was simply looking for help on how to install Firestarter. He didn't ask for any opinions on the program or anything to do with anti-virus software. I truly hope this childish bickering hasn't turned a new user away for life.

Way to hijack a thread,

---

