---
title: "Installing things - I saw a great guide once but I cant find it"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Tag_yer_dead on 2007-02-25
hey everybody,
im getting into linux and no how to work everything well enough, but i recently got a friend into it as well.  I learned from a great guide how to install things, if any one thinks they know where this guide is please paste a link.

Thanks

---

### Post by aysiu on 2007-02-25
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

or possibly
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by C-A on 2007-02-25
Who needs a guide when there is [Automatix]("http://www.getautomatix.com/")?!

---

### Post by PriceChild on 2007-02-25
> **C-A said:**
> Who needs a guide when there is [Automatix]("http://www.getautomatix.com/")?!automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu

---

### Post by Tag_yer_dead on 2007-02-25
lol thanks guys, that first dood has saved my life multiple times now.

Now second question for me lol, whats a way to totally uninstall an ap?
Isnt it something like - 
sudo aptitude --purge remove <app name>

Thanks

---

### Post by Maestro23 on 2007-02-25
> **PriceChild said:**
> automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu

Plus, when something happens to their servers and stuff is down, you have 100's of "The sky is falling" users crying on the forums because they dont' know how to do anything with their systems.:popcorn:

---

### Post by Maestro23 on 2007-02-25
> **Tag_yer_dead said:**
> lol thanks guys, that first dood has saved my life multiple times now.

Now second question for me lol, whats a way to totally uninstall an ap?
Isnt it something like - 
sudo aptitude --purge remove <app name>

Thanks

Yeah, that is one way. Good link to bookmark:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Tag_yer_dead on 2007-02-25
lol thanks again

---

### Post by C-A on 2007-02-25
> **PriceChild said:**
> automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu

My bad. I didn't realize that automatix was frowned upon. If I did, I would not have recommended it. :oops:

---

### Post by jackrobinson on 2007-02-25
> **C-A said:**
> My bad. I didn't realize that automatix was frowned upon. If I did, I would not have recommended it. :oops:

a very tiny bunch of forum members frown on automatix.. and if you observe carefully.. they make it a point to keep repeating their opinions .. I for one person recommend Automatix very strongly.

---

### Post by PriceChild on 2007-02-25
> **jackrobinson said:**
> a very tiny bunch of forum members frown on automatix.. and if you observe carefully.. they make it a point to keep repeating their opinions .. I for one person recommend Automatix very strongly.automatix broke a LOT of upgrades from dapper to edgy.

It is much better for you to install it yourself and learn how your system works.

i would personally say that almost all of the forum staff are against automatix, they just don't all voice it.

---

### Post by halitech on 2007-02-25
> **C-A said:**
> My bad. I didn't realize that automatix was frowned upon. If I did, I would not have recommended it. :oops:

personally I've used automatix and I've never had a problem with it as long as servers are running. It makes things alot easier to get a system up and running and usable but because they moved off, some that have a strong opinion, make it known that they don't like automatix. There is also easyubuntu for a script although I believe some people just feel that no one should use a script as it "dumbs down" linux. Personally, I feel that it is more important to get a system usable so people will keep using linux then it is that people use and learn how to install everything from the command line.

I'm sorry if I've stepped on some toes with my opinion but this is my opinion only and no one elses.

---

### Post by jackrobinson on 2007-02-25
> **PriceChild said:**
> automatix broke a LOT of upgrades from dapper to edgy.

It is much better for you to install it yourself and learn how your system works.

i would personally say that almost all of the forum staff are against automatix, they just don't all voice it.

It was not automatix Pricechild.. The Ubuntu devs were responsible for careless packaging which resulted in Dapper to Edgy upgrade failures. Its a well documented fact. A lot of false information was subsequently spread to make it look as if Automatix was responsible for the failures.. and unfortunately.. some people who never bothered to check, cling on to it (are you one of them too?).

---

### Post by jackrobinson on 2007-02-25
> **PriceChild said:**
> i would personally say that almost all of the forum staff are against automatix, they just don't all voice it.
I have noticed that most Ubuntu Forum mods are actually novice users who devote a lot of time to maintaining this forum. I wouldn't pay too much attention to what they think in this regard at least..

---

### Post by jackrobinson on 2007-02-25
> **PriceChild said:**
> automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu
also, what you actually quoted is straight out of the "mouth" of ubotu (the celebrated bot on #ubuntu). I checked a few months back and found out that the bot was actually written and maintained by "Seveas".  Seveas (though a noted contributor to Ubuntu) has had a VERY long history of bad blood with Arnieboy (the Team Lead of Automatix).. Doesn't this smell a bit funky to you?
Google "Seveas arnieboy".. you will know what I am talking about... all this has always reeked of very petty politics to me.. its unfortunate that a few people have blindly believed all the junk.

---

### Post by jdong on 2007-02-27
The bot is written by Seveas but the factoid database of the bots are approved by Ubuntu developers (specifically, the IRC ops subset). The view expressed is that of the Ubuntu developer community.

And "most of the staff" are not "novice users" and deserving your dismissal.

---

### Post by frodon on 2007-02-27
> **jackrobinson said:**
> It was not automatix Pricechild.. The Ubuntu devs were responsible for careless packaging which resulted in Dapper to Edgy upgrade failures. Its a well documented fact. A lot of false information was subsequently spread to make it look as if Automatix was responsible for the failures.. and unfortunately.. some people who never bothered to check, cling on to it (are you one of them too?).Really, did you already looked the automatix code ?

I did and it's also why the other ubuntu wikis make the same status, using automatix makes in some case your upgrade to fail because it uses unofficial packages and repositories.
That's nothing more than the reality and automatix devs still deny this.

For example the french ubuntu wiki :
[http://doc.ubuntu-fr.org/automatix](http://doc.ubuntu-fr.org/automatix)

---

### Post by matthew on 2007-02-27
> **jackrobinson said:**
> It was not automatix Pricechild.. The Ubuntu devs were responsible for careless packaging which resulted in Dapper to Edgy upgrade failures. Its a well documented fact. A lot of false information was subsequently spread to make it look as if Automatix was responsible for the failures.. and unfortunately.. some people who never bothered to check, cling on to it (are you one of them too?).What the devs stated was that if/when people install programs from places other than the official Ubuntu repositories then there is no way the devs can give support during an upgrade because there is no way for them to know how the non-repository installations may have affected the system as a whole. They did cite Automatix as an example of one method that a newcomer might install something from outside the official repos, but Automatix was not blamed for all upgrade failures. Sorry, that assertion is simply not true.

> **jackrobinson said:**
> also, what you actually quoted is straight out of the "mouth" of ubotu (the celebrated bot on #ubuntu). I checked a few months back and found out that the bot was actually written and maintained by "Seveas".  Seveas (though a noted contributor to Ubuntu) has had a VERY long history of bad blood with Arnieboy (the Team Lead of Automatix).. Doesn't this smell a bit funky to you?
Google "Seveas arnieboy".. you will know what I am talking about... all this has always reeked of very petty politics to me.. its unfortunate that a few people have blindly believed all the junk.Arnieboy has a gift for making relationships difficult. I know many people who have appreciated Arnieboy's work who also think he acts and speaks in a very arrogant and demeaning fashion. That's what smells funky...treating people poorly and then wondering why they don't like you. It's not petty politics at play here, it's basic relationship issues.

I don't have any particular opinion of Automatix as software nor as a tool. I've never used it. I do have a very well-formed opinion of Arnieboy.

---

### Post by jdong on 2007-02-27
[https://wiki.ubuntu.com/CommonCustomizations?highlight=%28automatix%29#head-f87ab027cad4d5a0ce0787c76b15f2188d41f9e7](https://wiki.ubuntu.com/CommonCustomizations?highlight=%28automatix%29#head-f87ab027cad4d5a0ce0787c76b15f2188d41f9e7)

Here is a Ubuntu developer analysis of what Automatix does. At this point almost everything Automatix does is safe to the system (it was not always that way, which could explain the developer aversion to Automatix. Bad 1st impression is always difficult to get rid of.)


However, in installation codecs and some programs it will go in and manually modify files in the /usr tree, bypassing dpkg (i.e. moving existing codecs out of the way, removing existing files to work around issues, etc), which is considered a no-no as far as system safety is concerned.

Be your own judge :)

---

### Post by marcelotmelo on 2007-02-27
There is a very good guide at the Unofficial Ubuntu Starter Guide, with repos and guides:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by matthew on 2007-02-27
> **marcelotmelo said:**
> There is a very good guide at the Unofficial Ubuntu Starter Guide, with repos and guides:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
That one's not bad.

This is also quite helpful: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by az on 2007-02-27
> **Tag_yer_dead said:**
> hey everybody,
im getting into linux and no how to work everything well enough, but i recently got a friend into it as well.  I learned from a great guide how to install things, if any one thinks they know where this guide is please paste a link.

Thanks

> **matthew said:**
> That one's not bad.

This is also quite helpful: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Let's not forget:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by jackrobinson on 2007-02-27
> **frodon said:**
> Really, did you already looked the automatix code ?

I did and it's also why the other ubuntu wikis make the same status, using automatix makes in some case your upgrade to fail because it uses unofficial packages and repositories.
That's nothing more than the reality and automatix devs still deny this.

For example the french ubuntu wiki :
[http://doc.ubuntu-fr.org/automatix](http://doc.ubuntu-fr.org/automatix)

Frodon: Thanks for replying. Yes, I have seen the code and as a matter of fact I have noticed that Automatix sticks to the official Ubuntu repositories as much as possible. It only seldom goes for unofficial packages and in rare cases, repositories when the dependencies involved are minimal. That itself shows how mature and safe the whole structure of the application is. I repeat, the upgrade failures were caused because of bad packages made by the Ubuntu devs. I myself was a victim of the same (on a machine which did not have automatix or any third party repo, it was a server).

---

### Post by jackrobinson on 2007-02-27
> **jdong said:**
> [https://wiki.ubuntu.com/CommonCustomizations?highlight=%28automatix%29#head-f87ab027cad4d5a0ce0787c76b15f2188d41f9e7](https://wiki.ubuntu.com/CommonCustomizations?highlight=%28automatix%29#head-f87ab027cad4d5a0ce0787c76b15f2188d41f9e7)

Here is a Ubuntu developer analysis of what Automatix does. At this point almost everything Automatix does is safe to the system (it was not always that way, which could explain the developer aversion to Automatix. Bad 1st impression is always difficult to get rid of.)


However, in installation codecs and some programs it will go in and manually modify files in the /usr tree, bypassing dpkg (i.e. moving existing codecs out of the way, removing existing files to work around issues, etc), which is considered a no-no as far as system safety is concerned.
<opinion>First impression is over-rated.. most folks who accuse others of mistakes are the ones who make the most themselves</opinion>
 
I rechecked the code in Automatix2 and did not find dpkg being bypassed anywhere (this was probably done in one or two cases in Automatix1) . I did see some broken packages being removed and replaced by statically linked binaries which actually work. I am sure the automatix devs have done this for a reason. They have tested to see what really works and going by the immense popularity of Automatix2 (inspite of all the unfounded FUD), what they do is probably right.

---

### Post by jackrobinson on 2007-02-27
> **jdong said:**
> The bot is written by Seveas but the factoid database of the bots are approved by Ubuntu developers (specifically, the IRC ops subset). The view expressed is that of the Ubuntu developer community.

And "most of the staff" are not "novice users" and deserving your dismissal.
Well the Ubuntu developer community also spreads misinformation trying to hide their own mistakes (this became very apparent during the Dapper to Edgy upgrade demise saga).. I still refuse to believe that this ratification by the Ubuntu developer is completely unbiased unless I see real proof. I have a feeling it all happened because Automatix acted independent of Ubuntu (or possibly Arnieboy's inter-personal issues?).

---

### Post by jackrobinson on 2007-02-27
> **matthew said:**
>  I do have a very well-formed opinion of Arnieboy.
Matthew:
I checked the reason why he was banned in the Resolutions Forum and I must say, I am not happy about the reason why he was banned. Sorry.. but thats how I feel.
I feel that one the biggest technical contributors on this forum should be treated with more respect (and not attacked).

---

### Post by frodon on 2007-02-27
Well, well, let's this thread go back on topic now, if you want to have a discussion about automatix please create your own thread.

Thanks.

---

### Post by jackrobinson on 2007-02-27
> **frodon said:**
> Well, well, let's this thread go back on topic now, if you want to have a discussion about automatix please create your own thread.

Thanks.
I agree.. We went vastly off-topic on this one. I rest my case hereon.

---

### Post by xpod on 2007-02-27
> personally I've used automatix and I've never had a problem with it as long as servers are running. It makes things alot easier to get a system up and running and usable but because they moved off, some that have a strong opinion, make it known that they don't like automatix. There is also easyubuntu for a script although I believe some people just feel that no one should use a script as it "dumbs down" linux. Personally, I feel that it is more important to get a system usable so people will keep using linux then it is that people use and learn how to install everything from the command line.

I'm sorry if I've stepped on some toes with my opinion but this is my opinion only and no one elses.

I`ve also voiced my favourable opinion of AX on more than one occasion but only because  i dont really believe people learn any less by using the thing as i`ve seen said,especially to start out with.

It can have\cause problems just as anything else can i`m sure, but it can surely also save more problems than it creates in many cases and i reckon it`s probably helped more noobs than it`s hindered along the way.Those same noobs mabey do fine now without AX now but were thankfull for it at the time?..........what do i know though eh??

I dont give two hoot`s if people dont like my opinion as my opinion dont matter but it was on these forums that i too was directed towards AX and it`s never caused me any problems on any setups\pc`s,and it`s certainly never stopped me learning how to install stuff the numerous other ways either....or anything else come to that

If i think it`s the best choice for someone in the situation at the time(wanting more than frorstwire) i will recommend it still and If people do have problems with it then mabey the experts could just help them out instead of berating them for having used AX in the first place.:) 

AX is OK:tongue:

---

