---
title: "VoiceoverIP in Ubuntu?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Archmage on 2007-08-28
Is there an open source client for VoiceoverIP that I can use in Ubuntu?

I would prefer it, if they are in the repo.

---

### Post by mikewhatever on 2007-08-28
Ekiga is preinstaled, and wengo phone is in the repos. There is also Gizmo and others I can't remember atm.

---

### Post by yabbies on 2007-08-28
I know Skype has a deb package on their website.

didn't read this but looks like a good article to get you started.

[Linux Journal]("http://www.linuxjournal.com/article/8853")

---

### Post by laidback on 2007-08-28
Skype, from repros for 7.04. pc to pc free. Need an a/c for pc to landline.
Ekiga (default app in 7.04) and Viopstunt for pc to landline. Need to create a/c for Voipstunt via windoz as software doesn't run in Linux. But once done it works.

---

### Post by por100pre1 on 2007-08-28
[Gizmo Project]("http://www.gizmoproject.com/"), works on a SIP network and comes in a deb package tested on Ubuntu.

---

### Post by YannickDefais on 2007-08-29
Hi,

Ekiga has a nice documentation to get you started here:
[https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)

Regards,
Yannick

---

### Post by loell on 2007-08-29
+1 for gizmoproject though closed source, it adheres to sip standards, with the right settings from contacts from your yahoo or and windows live messengers, you can also do voice call with those networks.

it also achievable in ekiga,  twinkle and linphone.

---

### Post by YannickDefais on 2007-08-29
> **loell said:**
> +1 for gizmoproject though closed source, it adheres to sip standards, with the right settings from contacts from your yahoo or and windows live messengers, you can also do voice call with those networks.

it also achievable in ekiga,  twinkle and linphone.

Hi,

EDIT: Oops, yes gizmo can do voice call to those proprietary networks...
EDIT2: In fact Gizmo uses the same trick as described below : [http://forum.gizmoproject.com/viewtopic.php?p=35182](http://forum.gizmoproject.com/viewtopic.php?p=35182) with probably just a better integration.

For Ekiga, Twinkle, and linphone I disagree :
The reason is all those softwares use SIP for VoIP. Yahoo, WLM use there own private protocole for VoIP. Thus you need some kind of converter to reach their proprietary networks.

This is possible to do a voice call from ekiga to yahoo or MSN or GoogleTalk users using this service:
[http://www.gtalk2voip.com/](http://www.gtalk2voip.com/)

You can even use a special package like this one for this purpose:
[http://ubuntuforums.org/showthread.php?t=431290](http://ubuntuforums.org/showthread.php?t=431290)

Alternatively, you also can use [http://www.freeswitch.org/](http://www.freeswitch.org/) to connect a SIP client (like Ekiga, gizmo, twinkle, linphone, etc.) to GoogleTalk. In this solution you don't rely on an external service (who knows what will do gtalk2voip.com in the future ?).

Regards,
Yannick

---

### Post by laidback on 2007-08-29
I have it running with Ekiga, see here for setup info:-

[http://ubuntuforums.org/showthread.php?t=450394&page=3](http://ubuntuforums.org/showthread.php?t=450394&page=3)

---

### Post by niceguy123 on 2007-09-07
Hi,

I think that I configured Ekiga with my Skype account, but I'm not sure if Ekiga is working altogether. The Ekiga control opens up, but I don't see a contact list tab.

---

### Post by ubuntukerala1980 on 2007-09-07
i use skype :guitar:

See this[https://help.ubuntu.com/community/Skype]("https://help.ubuntu.com/community/Skype")

---

### Post by niceguy123 on 2007-09-07
> **kiran.bhaskaran.nair said:**
> i use skype :guitar:

See this[https://help.ubuntu.com/community/Skype]("https://help.ubuntu.com/community/Skype")

Thanks, I would like to use Skype within Ekiga. I'm not sure about the Skype configuration in Ekiga. And I'm also not sure about Ekiga. 

BTW - I'm new to Ubuntu.

---

### Post by por100pre1 on 2007-09-07
The main problem with Skype is that it uses a proprietary protocol, SIP networks, devices and software are a best alternative for serious VOIP use. Skype has taken heat for other issues like its super node behavior, and user accounts hijacked from the servers.

---

### Post by YannickDefais on 2007-09-07
Hi,

There is no way you can use your Skype account with Ekiga. Skype don't allow that. At least for free.

Regards,
Yannick

---

### Post by niceguy123 on 2007-09-08
> **YannickDefais said:**
> Hi,

There is no way you can use your Skype account with Ekiga. Skype don't allow that. At least for free.

Regards,
Yannick

Thanks for pointing that out. It seems that there are a whole bunch voip servers and a couple of types of interface that combine some of them. 

Which is the best? (I'm new here) I've stated using pidgin for IM on one platform and really enjoy the idea of not having to cutler up my work space with different tools to communicate with people on AIM, ICQ and googlechat, How can I do the same with VOIP?

Another question: is there a service that gives pc to landline for free? (yeh, I know nothing is for free, but though I'd ask anyway).

---

### Post by YannickDefais on 2007-09-08
Hi,

Well, this is at least 6 major voIP protocols:

Standards protocols:
 - SIP (Ekiga, Gizmo, Windows Messenger, Wengophone, x-lite, xmeeting,... use it)
   This is the actual standard (IETF standard = web standard)
 - H323 the old standard, not really deprecated, but SIP is much more in use today
 - GoogleTalk, it use an extension to the Jabber protocol, it will probably become a standard too, with GNU/Linux Jabbin can use it (voice only)

Proprietary protocols:
 - Skype , only Skype can use it (no video yet using GNU/Linux)
 - Yahoo messenger
 - MSN, Windows messenger

There is a free software running under GNU/Linux to transcode SIP <-> GoogleTalk : freeswitch [http://www.freeswitch.org/](http://www.freeswitch.org/) But, I would say it's not yet user friendly

There is free (as free beer) web service to transcode SIP <-> Yaho <->MSN <-> GoogleTalk [http://www.gtalk2voip.com/](http://www.gtalk2voip.com/) (but it only do audio) (Gizmo has it as a built in feature under the name "Meta Voice").

The software [http://gyachi.sidetrack.googlepages.com/](http://gyachi.sidetrack.googlepages.com/) use Ekiga + gtalk2voip.com to provide a way to do VOIP with yahoo messenger ; see this thread : [http://ubuntuforums.org/showthread.php?t=431290](http://ubuntuforums.org/showthread.php?t=431290)

As far as I know this is the actual state of art for VoIP using GNU/Linux

Result: If you want to use Skype, you must use Skype under Linux (no video)

About video : 
SIP can do video under Linux, you have 3 solutions (they all use SIP but different video codecs):

Video codec - Linux   -   Windows   -   Mac OS
h261 - Ekiga  -   Windows Messenger 5.1 (This is NOT MSN) or Ekiga for windows   -  Xmeeting
h263 (not standard) - Wengophone   -   Wengophone   -    Wengophone
h263+ - Linphone   -   x-lite   -    x-lite

Jabbin (like googletalk) can't do video.

There is no way to have audio with MSN/Windows Live Messenger.

I will soon explain all this in the community documentation (I just need to translate it from my french documentation and more spare time)


To call landline, SIP is the cheapest, see this comparison chart (in french sorry):
[http://www.voipfr.org/comparateur/](http://www.voipfr.org/comparateur/) 
("gratuit" means free
[F] means landline
[M] means cell phones
États-Unis means USA
Opérateur means Provider)

Or this one (only betamax providers SIP)
[http://backsla.sh/betamax](http://backsla.sh/betamax)

Regards,
Yannick

---

### Post by niceguy123 on 2007-09-08
I've followed the Ekiga set up instructions ([https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)) 

But when I try this: 
> When you're done the druid and if you have an account on [WWW] ekiga.net, you can call the echo test: sip:500@ekiga.net You'll be able to check if you can reach the service (the SIP network), if your sound setup is ok (you can hear yourself with a delay) 

I hear a two or three rings and then it changes to a fast busy tune and on the bottom of the window it says > abnormal call termination 


I've checked edit>accounts and see there that status is listed as registration failed, I tried the same login info on the ekiga.net and got in. What am I missing?

---

### Post by YannickDefais on 2007-09-09
Hi,

Maybe you used special chars in you password, please only use letters and numbers (this is a bug).

Or if it's not that, please post a debug output somewhere on the net (like here [http://pastebin.ca/](http://pastebin.ca/) )
like this:
[http://wiki.ekiga.org/index.php/Debugging_Ekiga#How_to_get_a_debug_output_from_Ekiga](http://wiki.ekiga.org/index.php/Debugging_Ekiga#How_to_get_a_debug_output_from_Ekiga)
reproduce the step you've done until the abnormal call and post the resulting file.

Regards,
Yannick

---

