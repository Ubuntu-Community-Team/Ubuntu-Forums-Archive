---
title: "Free phone calls to landlines!!!!"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by laidback on 2007-05-21
My daughter has just phoned me via VOIPSTUNT, a free to landline voip system. As I use skype which takes payments for landline calls I investigated. But it would appear that voipstunt only works with W2000, XP, Vista. Does anyone know of a similar system that does work with Ubuntu?

---

### Post by Nekiruhs on 2007-05-21
Have you tried using Wine?

---

### Post by frodon on 2007-05-21
Ekiga support all open voip protocols so you can surely use VOIPSTUNT with ekiga, ekiga is made for this purpose.
Look in Application > Internet > softphone ekiga it's installed by default ;)

---

### Post by Nekiruhs on 2007-05-21
If anyone gets it working with Ekiga, please post here how.

---

### Post by Jussi01 on 2007-05-21
Gizmo has free calls undersome circumstances, your best off reading their website. [www.gizmoproject.com](www.gizmoproject.com)

Cheers, 


Jussi

---

### Post by pospam on 2007-05-21
Hi:
I found this tutorial on how-to get ekiga to work with voipcheap, which by the way
run by the same people as VOipStunt.
<snip - dead link>  
I haven't tried it, but I think you just need to change some basic things like server, etc
I quick search in the voipstunt web site gave this information you might find useful.

Software configuration
General
	SIP port : 5060
	Registrar : sip.VoipStunt.com
	Proxy server : sip.VoipStunt.com
	Outbound proxy server : leave empty
	Account name : your VoipStunt username
	Password : your VoipStunt password
	Display name/number : your VoipStunt username or voipnumber
	Stunserver (option) : stun.VoipStunt.com

Hope this helps
P.

---

### Post by frodon on 2007-05-21
> **Nekiruhs said:**
> If anyone gets it working with Ekiga, please post here how.Just add your voipstunt account to ekiga.
[IMG]http://ekiga.org/admin/screenshots/latest/Ekiga_Accounts.png[/IMG]

    * Account name : voipstunt
    * Protocol : sip
    * Registrar : sip.voipstunt.com
    * User : ********* the one you get on voipstunt.com
    * Password : ************
    * Domain : voipstunt.com

Then to call type the number like that : sip:012345678@sip.voipstunt.com, you may need to add your country code before the phone number.

That's all ;)

There's also voipcheap which is not bad, a full guide is available here :
[http://doc.gwos.org/index.php/Ekiga_voipcheap_account](http://doc.gwos.org/index.php/Ekiga_voipcheap_account)

Enjoy :)

---

### Post by laidback on 2007-05-21
Wow what a response. I knew you'd have some suggestions. Never thought of using Wine, in fact I've never used that at all.
Think I'll look into ekiga first.

Many thanks one and all. This will keep me busy for a while.

---

### Post by plainjane on 2007-05-21
Hey, thanks for the heads up about voipstunt.  I had never heard of it before.  I just told my son at college about it, and in just a couple of minutes he called me!  I love this forum, I learn something new every day!  Many thanks again!

---

### Post by Hallvor on 2007-05-21
Perhaps a stupid question, but is it possible to get a username and password *without* downloading the software? I haven`t got Windows.

---

### Post by laidback on 2007-05-21
I must be really thick. Looked into this:-

There's also voipcheap which is not bad, a full guide is available here :
[http://doc.gwos.org/index.php/Ekiga_voipcheap_account](http://doc.gwos.org/index.php/Ekiga_voipcheap_account)

which was posted by frodon. Went to the voicecheap ref#, but how do you register an account, all I can find is a download, which is an exe file, cannot run that on my Ubuntu system can I?

---

### Post by laidback on 2007-05-21
Happvor,

My question too, cannot find a way of getting an account without downloading the exe file, which wont run in Ubuntu.

---

### Post by frodon on 2007-05-21
> **laidback said:**
> Went to the voicecheap ref#, but how do you register an account, all I can find is a download, which is an exe file, cannot run that on my Ubuntu system can I?According to the FAQ it seems indeed that you need windows once to create an account, what a pity :( :
[http://www.voipcheap.com/en/faq.html#12](http://www.voipcheap.com/en/faq.html#12)

---

### Post by laidback on 2007-05-21
Have installed wine and ran the exe downloaded file. It ran, installed a Voipcheapicon on the desktop.....so far so good, but I still don't have an account. We're getting somewhere though. The icon doesn't appear to do anything!

---

### Post by laidback on 2007-05-21
The desktop icon wants to run this:-

env WINEPREFIX="/home/david/.wine" wine "C:\Program Files\VoipCheapCom\VoipCheapCom.exe"

which it doesn't do. Tried running the file from within Wine File but that hasn't achieved anything I can see. Part of the problem is I know nothing about wine, could I expect it to run the exe file from within the file manager?

---

### Post by scrooge_74 on 2007-05-21
The only catch is in order to use VOIPSTUNT you need to download the software on an Windows PC in order to register...if I have a change today I will download it on another PC at work which has dual boot and register with them so I can use Ekiga

---

### Post by scrooge_74 on 2007-05-21
> **laidback said:**
> The desktop icon wants to run this:-

env WINEPREFIX="/home/david/.wine" wine "C:\Program Files\VoipCheapCom\VoipCheapCom.exe"

which it doesn't do. Tried running the file from within Wine File but that hasn't achieved anything I can see. Part of the problem is I know nothing about wine, could I expect it to run the exe file from within the file manager?

Better try it from the command line wine VoipCheapCom.exe

But I am not sure it will run anyway

---

### Post by laidback on 2007-05-21
Tried running from the CL wine ...... no luck, lots of errors.

Really don't want to use the XP box...ahhhhh!!!!

---

### Post by kittyhawk63 on 2007-05-21
[COLOR=Red][B][SIZE=1]Jajah[/SIZE]
      JAJAH
              [/B][/COLOR][COLOR=Red][B][SIZE=3]JAJAH[/SIZE]
                        [/B][/COLOR][COLOR=Red][B][SIZE=4]JAJAH[/SIZE]
                                    [/B][/COLOR][COLOR=Red][B][SIZE=5]JAJAH
                                [/SIZE][/B][/COLOR][SIZE=6][COLOR=Red][B]JAJAH
                                 [/B][/COLOR][/SIZE][SIZE=7][COLOR=Red]**JAJAH**[/COLOR][/SIZE]
[COLOR=Red][B]
[COLOR=Black]Need I say more?[/COLOR]
[/B][/COLOR]

---

### Post by laidback on 2007-05-21
Got it working!!!!!!

I'll post the method later as I'm off to have tea now.

---

### Post by laidback on 2007-05-21
I now have** Voipstunt working via Ekiga**. I owe the solution to frodon who posted the basic solution above. Should you be interested please note the following:-

Check that your microphone is working, I used Sound Recorder for this.
Install Ekiga, unless you already have it as per 7.04 users.
Get to a Windoz box to create your Voipstunt a/c. (Sorry yes windoz ahhh!)
Visit the Voipstunt web site and download their exe file
Run the file on your windoz box in order to create the account
Note the username and password that you created (you will receive an email confirmation of these)
Shutdown windoz (hurrah), back to Ubuntu
Open Ekiga, you may get a first time wizard
No need to create an Ekiga a/c so you can refuse this (early splash screen)
Follow the Wizard through, it'll search for your NAT, mine chose STUN server whatever that is, I accepted defaults
In Audio devices I chose what I knew to work from my tests with Sound Recorder, you can ask it to detect devices
I ignored Video devices as I don't have a camera
All these settings can be adjusted later via Ekiga>Edit>Preferences

Create an account:-
	Account name:	voipstunt  (think this is just a reference so could be anything)
	Protocol:	     SIP
	Registrar:	    sip.voipstunt.com
	User:		      your_voipstunt_user_name_as_you_noted_down
	Password:	 your_voipstunt_password

press More to expand lower section

	Authentication login:	your_voipstunt_user_name ( as in User above )
	Real/Domain:		voipstunt.com

press OK

back at the Account screen click left hand box of your new account (column A) to get the account Registered. You should see your internet lights flashing as something rushes off to check your a/c. Hopefully it'll come back with REGISTERED, press Close and you're away. If you get NOT registered go back and check your typing etc (I had to do this several times as I kept making mistakes) In fact I deleted the account altogether and started again, no harm done.

After all that I was left with the Ekiga dialling pad on the desktop. It seems to park in the system tray.
Typed in my own home number (exactly as I would on a landline phone, no country codes etc. )
Pressed the call button (right hand side of where you typed in the number, looks like a plug and socket)
Waited for some odd clicks and bangs. It actually tells you what's going on in the bottom section of the screen.
And then, WOW my phone rang.

I've tried 4 calls so far. All Local/National UK calls. All worked. I'm getting used to the connection noises now.

In the Email you get from Voipstunt there are some sites to visit, one talks about buying credit. I visited this and had a look at my account details. It confirmed that all my calls were free. Think the credit allows for international/mobile calls etc. You can text as well.

So far so good. I think I could improve the sound quality by heh, it's just fantastic anyway.

Thanks to all of you who replied and especially frodon who's ideas I used.
plainjain:  glad to have been of help. I really enjoyed the success you have had as a result of this POST.


Kindest regards to you all

Laidback

---

### Post by Chemroydal Tissue on 2007-06-13
OK, so what's the catch? I see that if you go over 300 minutes (EDIT: per week) they charge you. I don't think I use 300 minutes/month! This could save me a couple hundred bucks/year. Anyone used this service for awhile and/or encountered any problems (spam/unwanted calls to either you or the people you call, etc.)?

---

### Post by sdowney717 on 2007-07-21
I have it running bur I dont know how to make a call work.

I am in the usa, so what I was trying to do is

sip:757886xxxx

and 

sip:011757886xxxx

but I get the number cant go thru please check number and dial again.

What is the right format to use when calling to a USA phone number?

---

### Post by kc5hwb on 2007-07-21
Thanks for bumping this thread, this is awesome.  I am going to sign up now  ;)

sdowney717 - did you try just a "1" in front of the #, rather than the "011" int'l code?

---

### Post by sdowney717 on 2007-07-21
thanks, that worked.

But, IMO, the sound quality is not good.

When you setup the account in Ekiga, check the box and it will register, something all the quides seem to have left out.

---

### Post by sdowney717 on 2007-07-21
I just called our cell phone using Ekiga and voipCheap.
The cell phone has excellent sound quality. As good as a normal call would be sounding.
The desktop computer speaker sound is not very good.
Dont tell me it is feedback loop, I can unplug the microphone and the speaker quality is the same.

The PC speaker has a wavery type of tremulous sound to it. Does anyone of you know how to improve it?

---

### Post by sdowney717 on 2007-07-21
I improved it tremendously by setting the sound setteings in Ekiga from default which was in the wiki guide to the intel ich4 listed in the drop down box in ekiga.
So dont put it on default!

It does have the echo now and I think a headset would fix that. This is a great deal for a VOIP softphone in Ubuntu.

---

### Post by ramjet_1953 on 2007-07-22
After registering on a Windows box, I then put the information into Ekiga and it worked straight-up.

Regards,
Roger :cool:

---

### Post by gn2 on 2007-07-22
> **sdowney717 said:**
> I improved it tremendously by setting the sound setteings in Ekiga from default which was in the wiki guide to the intel ich4 listed in the drop down box in ekiga.
So dont put it on default!

It does have the echo now and I think a headset would fix that. This is a great deal for a VOIP softphone in Ubuntu.

A headset is pretty much essential for VOIP to prevent the microphone from "hearing" the speakers.

Alternatively you can  buy a SIP phone device which is independent from the PC and just use it like a normal phone.

Voipcheap has changed it's call charge price structure from the original offering, it's sister company [http://www.12voip.com/en/index.html](http://www.12voip.com/en/index.html) may suit some people better.

You can use Voipcheap with your conventional landline phone using it's web interface which also allows you to send SMS text messages.

I have been using Voipcheap for a year or so and it is excellent.

---

### Post by laidback on 2007-07-22
I'm very pleased to see that this thread continues to provide useful information to users. Many thanks to all those that have added value to the orignal POST.

Laidback

---

### Post by sdowney717 on 2007-07-22
some practical ease of use observations, is there a way to:

buy or make a headset from an old phone using its internal microphone and speaker

buy a usb phone and use that to dial calls or even just basically talk?

buy a usb to phone port adapter and use a conventional land phone?


anyone have any product source or info to share ?

I was thinking a headphone you will either have to unplug your speakers everytime you want to call or make a speaker output splitter? Then turn off your main speakers. But would this blow out the headset ear speakers?

---

### Post by ADT on 2007-07-22
Cool, I'm definitally going to try this.

---

### Post by jvc26 on 2007-07-22
Thanks very much for this, an excellent post, very helpful.
Il

---

### Post by arochester on 2007-07-23
I couldn't get this to work with Ekiga - but  I got it to work with X-lite

---

### Post by sdowney717 on 2007-07-24
well I ran out of free calls so they want me to buy credit. So I click thru and they want 10 euros. So free is a relative term. 10 euros buys 90 days of free calls not to exceed 300 minutes per week.

I wont do this as I have a cell phone with unlimited calling and a VOIP home phone with unlimited calling. But it was interesting to try it out and see it work.

---

### Post by eugenia on 2007-08-08
VoIPCheap appears to be not exactly what it would have you believe from it's web site - beware.

This statement

"You can now make FREE calls to several countries. These calls are limited to 1 minute per call.
If you want UNLIMITED calls to our FREE destinations please go to our website and buy credit."

Does not appear on the web site as far as I can see. Add to the above this from the FAQ and you might get a better idea of what it is all about.

"Buying credits entitles you to 90 Freedays (unless stated otherwise). This means you can call all countries in the free* destinations list for 90 days at no costs. When the 90 days are over, you will keep your credit, and the normal rate will be charged for these destinations."

---

### Post by gn2 on 2007-08-08
> **eugenia said:**
> VoIPCheap appears to be not exactly what it would have you believe from it's web site - beware.



VoipCheap is a reputable and excellent facility, however 12voip may suit better.
[http://www.12voip.com/en/index.html](http://www.12voip.com/en/index.html)

---

### Post by YannickDefais on 2007-08-10
Hi,

All the VoIP services you guys mentioned belong to one big company : Betamax

They all basically work the same way, just prices change ; see this price chart:
[http://backsla.sh/betamax](http://backsla.sh/betamax)

As they all require to install they very own private softphone on windows to get username and password, I do not want to include them in the documentation [https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)

To get good sound in Ekiga:
Yes, you can select your sound card directly instead of "default" in the ekiga preferences. Just be aware: if Ekiga start using your sound card in this setup, no other application will be able to use it until Ekiga stops using it.

"Default" use ALSA sound system ability to mix sound before using the sound car (technology called "DMIX" and "DSNOOP" in ALSA), thus any audio application can run with ekiga. The DMIX technology is knew to be problematic. Let's hope thing are improving in this area now.

The echo cancellation option in Ekiga preferences (Audio codecs) may cause problems, disable it to see if sound improve.

If none of the previous settings helps you getting better sound quality, Ekiga shipped with Ubuntu (2.03 at best) has a serious bug with some sound cards, please upgrade to 2.0.9 (just stable and bug fixes releases) using this:
[https://help.ubuntu.com/community/Ekiga#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c](https://help.ubuntu.com/community/Ekiga#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c)

Regards,
Yannick

---

### Post by tramir on 2007-08-19
Hey guys,
Did anybody manage to get 12voip working with Ekiga? Here's where I'm at: I opened an account from a Window box. Then, I found somewhere that the server seems to be the same as for the other voipbuster (or stunt?) clones, so I just put in "sip.voipstunt.com" as the registrar's address. I do get registered, but no calls go through. I either get a "remote user rejected the call" or an "abnormal call termination" error. Any ideas? TIA...

---

### Post by elias85 on 2007-08-22
hey that 12voip rules! anyone to give info on how to make that work?

---

### Post by philinux on 2007-08-22
Just looked at the ekiga app.

Noob to voip, what hardware does one need like a special phone where does it connect?

---

### Post by em007a on 2007-08-22
Silly question I guess, but I have never used voip before. 

If I have a cell phone with unlimited long distance and minutes, is there any reason to use voip? 

And what is the typical costs to use voip to call landlines?

Thanks.

[quote=Philinux] Noob to voip, what hardware does one need like a special phone where does it connect?[/quote]Af far as I can tell, you just need a microphone and speakers (or headset is recommended).

---

### Post by AgentZ86 on 2007-10-20
> **em007a said:**
> Silly question I guess, but I have never used voip before. 

If I have a cell phone with unlimited long distance and minutes, is there any reason to use voip? 

And what is the typical costs to use voip to call landlines?

Thanks.

Af far as I can tell, you just need a microphone and speakers (or headset is recommended).

Well, it's all different, 

I use Vonage for my VOIP and it's unlimited calling for long distance/international and local for $24.00 US per month, so thats very reasonable, for any phone land cell etc. 

But for these softphone VOIP basically if you call another VOIP softphone users that is free sort of like IM's on the net, no fees,charges etc. it's only the landlines  and cells that people have to get creative with in order to either get it for free or for very small fees for international calls.

That the benifit, the international calling is the main savings feature in my opinion

Anyhow thats all I know.

---

### Post by Dr Small on 2007-10-20
> **ramjet_1953 said:**
> After registering on a Windows box, I then put the information into Ekiga and it worked straight-up.

Regards,
Roger :cool:
I haven't got a windows system... anyone care to register an account for me, and then I can change password ?

---

### Post by AgentZ86 on 2007-10-26
> **Dr Small said:**
> I haven't got a windows system... anyone care to register an account for me, and then I can change password ?

I think soon I'm going to put an old windows box in the corner and share the desktop for anyhow who wants to do little tasks like this that require windows.

I mean a sort of internet shared complete computer. I realize it may get hacked or messed up from people just trying to be funny but it would be nice just for these types of things.

Anyhow I'll try after the weekend and boot up to windows Then register you; and I'll use your msn address for registration and you can then login I guess to edit the password or something.

Anyhow FYI I'll fool with it on Mon. / Tues.

---

### Post by rakusson on 2008-03-30
thanks now I can use VoipStunt accounts to make call through Ubuntu. Thanks all of you guys and Ekiga.

---

### Post by iheartubuntu on 2008-06-13
Using VoipStunt with Ekiga, but Ekiga disappears (crashes) after a call gets placed. I know its somewhat working since I can hear my phone ringing, but Ekiga on Ubuntu 8.04 is crashing. Any tips?

Now, what the heck was I going to do before i came across this thread???

---

