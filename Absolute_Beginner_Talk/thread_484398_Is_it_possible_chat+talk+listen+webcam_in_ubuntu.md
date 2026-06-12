---
title: "Is it possible chat+talk+listen+webcam in ubuntu?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by cseljatib on 2007-06-25
I want to replicate the same thing that I did using MSN in windows, that is to say: be able to chat+talk+listen+webcam

I have tried with GAIM, but does not have video, and as far as I know, I could set up google talk to work on that, but I will not have webcam.
I have also tried with aMSN, and I am able to have webcam connection (and working OK), however, neither I can talk nor to listen.

Any suggestion, PLEASE?
thanks in advance

---

### Post by windows hater on 2007-06-25
well i have the same problem but i was told there is no one im client to do all u want so u have to use skype which would be ur  voice and amsn for video

---

### Post by ramjet_1953 on 2007-06-26
Follow this link to WengoPhone:

[http://www.openwengo.org/](http://www.openwengo.org/)

It pretty much does everything that Skype does, including calls to regular telephones and video chat.

Regards,
Roger :cool:

---

### Post by cseljatib on 2007-06-28
OK, thanks, but I cannot get my MSN contacts in Wengo, do you how should I do that?

---

### Post by girard on 2007-07-02
i'm also still trying to look for that client to use for communication. the problem is that the other end of the chat/video/call has to have the same application right? for example, all of my contacts are from yahoo. is it possible to establish a video call with them using Y!messenger on the other end (all MS users!) and ubuntu (whatever client) on mine?

this was my problem a couple of months ago, and that's why i use my notebook most of the time (windows) because i can't make video calls to my contacts.

---

### Post by Motoxrdude on 2007-07-02
Have you tried downloading the yahoo messenger exe and running it in wine?

---

### Post by chele on 2007-07-03
> **girard said:**
> .. is it possible to establish a video call with them using Y!messenger on the other end (all MS users!) and ubuntu (whatever client) on mine?No. You can only text chat with users on the Y! network using gaim/pidgin, the standard Ubuntu IM application. 

There is no video IM client for Linux that can connect to the Y! network. That is the way Y! wants to keep it.

The native Ubuntu Linux video call client is Ekiga. Users stuck with MS Windows on their computers can use Windows Messenger (not Live nor MSN messenger) or the windows version of Ekiga. Ekiga uses the SIP protocol, rather then the private protocols used by Y! and MSN.

---

### Post by wolfen69 on 2007-07-05
Gyachi- [http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)  is a yahoo messenger clone that supports audio/webcam etc. best one ive seen. is available in synaptic.

---

### Post by mano3891 on 2007-07-07
Why dont u try Kopete? I use Kopete for aim, msn and yahoo and I often video chat in yahoo. Hope this helps!!!

Mano

---

### Post by forrestcupp on 2007-07-07
> **mano3891 said:**
> Why dont u try Kopete? I use Kopete for aim, msn and yahoo and I often video chat in yahoo. Hope this helps!!!

Mano

+1

Kopete will do video for msn and yahoo.

---

### Post by punong_bisyonaryo on 2007-07-07
In summary, Wengo, Gyachi, and Kopete is suggested. Personally, I'm biased towards Gyachi and Kopete, because I can connect to YM clients. I assume Kopete is KDE? What are Wengo's strong points that would make me want to consider it over the other two?

Thanks!

---

### Post by ramjet_1953 on 2007-07-08
Strong points is a subjective thing, depending up what your own needs are.

However, if you want these features, WengoPhone may be for you:

1. You can dial regular land line telephones, just like Skype.

2. It has encrypted call capability.

3. You can make video calls (Skype for Linux cannot)

4. It is Open Source and uses SIP addresses, not a propriatory system like Skype. SIP allows you to be able to contact any SIP user, regardless of system, even people who have a SIP-based PABX system, that has connection to the Internet.

5. You can SMS mobile phones

6. ALSA support

7. Runs on Windows, Mac and Linux.

There are probably lots more.

Regards,
Roger :cool:

---

### Post by loell on 2007-07-08
> **punong_bisyonaryo said:**
> In summary, Wengo, Gyachi, and Kopete is suggested. Personally, I'm biased towards Gyachi and Kopete, because I can connect to YM clients. I assume Kopete is KDE? What are Wengo's strong points that would make me want to consider it over the other two?

Thanks!

wengo is also aiming to be like kopete, a multiple IM client,  but its not there yet.. one advantage with wengophone over kopete though is its a softphone by default.. 

like all standard softphone clients, it still can not call yahoo/MSN natively.. nor does it do webcam in those networks.

---

### Post by punong_bisyonaryo on 2007-07-08
> **ramjet_1953 said:**
> 3. You can make video calls (Skype for Linux cannot)


I'm trying out Kopete right now. As far as it goes, I can do video chat with my YM buddies, but no sound. Preferably, I want a client that can connect to Y!, do video and at the same time voice. Aside from the Wine option (which is to me, unnacceptable), is there any linux client that can do this? I also tried Wengo, can it connect to Y!?

---

### Post by loell on 2007-07-08
AFAIK, no single client can do this with those close networks, however  there is a free service that lets you call
Yahoo Messenger and Windows live messenger on any standard softpone..

[URL="http://ubuntuforums.org/showthread.php?t=414121"]  	   	
HOWTO: Voice call Yahoo Messenger using Ekiga and gtalk2voip service.[/URL]

or try gizmo phone , it also uses this service..



**so, well you know, just consolidate two apps to achieve video and voice ;)**

---

### Post by punong_bisyonaryo on 2007-07-08
Since both ekiga and Kopete and wengo are open source applications, hasn't anyone thought of getting the best of each of their worlds and putting it in their application?

(Why don't I do it? I don't know how to program linux apps yet, soon I hope)

---

### Post by loell on 2007-07-08
:-k , not sure what you mean by best of both worlds..

but wengo is a SIP softphone which much like Ekiga only Qt based, and tries to mimick kopete's function as multi IM client.

---

### Post by punong_bisyonaryo on 2007-07-08
> **loell said:**
> :-k , not sure what you mean by best of both worlds..

but wengo is a SIP softphone which much like Ekiga only Qt based, and tries to mimick kopete's function as multi IM client.

Sorry, i meant that wengo can do voice calls, and kopete can do video. if wengo can get the video chat functions of kopete, wouldn't that be cool?

---

### Post by punong_bisyonaryo on 2007-07-08
And I can't seem to find where I can add YM contacts to Wengo.

---

### Post by loell on 2007-07-08
ah.. yeah.. you mean Yahoo and MSN video ? 
i think this is one of wengo's todo list, it may take a while to incorporate this though.

lets just pray [-o< , that someday jabber  will overthrow these proprietary protocols , and we won't have to worry about different implementations.

if everybody will just use jabber for voice / video ( a libjingle like implementation) and share drawing boards and such , oh what a perfect world will it be. :popcorn:

---

### Post by loell on 2007-07-08
> **punong_bisyonaryo said:**
> And I can't seem to find where I can add YM contacts to Wengo.

theres a caveat in using y! and msn accounts in wengo :( , you must have sip account or wengo account , then after you log in,  in tools menu --> configuration --> accounts add your Yahoo account..

your y! contacts will then appear , another thing that i find strange is that you cant send an offline message to your Y! offline buddiess :( , the UI is also misleading the users, by giving a phone icon into your Y! contacts , when in fact it means, that you have to add a phone number to that y! contact..

---

### Post by punong_bisyonaryo on 2007-07-08
> **wolfen69 said:**
> Gyachi- [http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)  is a yahoo messenger clone that supports audio/webcam etc. best one ive seen. is available in synaptic.

What repository is it available from? I'm using Edgy, with all repositories enabled, plus medibuntu repository.

---

### Post by punong_bisyonaryo on 2007-07-08
> **loell said:**
> in tools menu --> configuration --> accounts add your Yahoo account..

I can't even find that. There isn't a tools menu, nor accounts in configuration.:(

---

### Post by loell on 2007-07-08
> **punong_bisyonaryo said:**
> I can't even find that. There isn't a tools menu, nor accounts in configuration.:(

you must be using the wengophone from edgy repo?

i'm currentlty testing this wengophone v2.1.1

---

### Post by loell on 2007-07-08
> **punong_bisyonaryo said:**
> What repository is it available from? I'm using Edgy, with all repositories enabled, plus medibuntu repository.

gyachi isn't available in ubuntu repos, but you can find a deb package for edgy at gyachi's download site, and its also available in automatix.

---

### Post by punong_bisyonaryo on 2007-07-09
I don't suppose you can tell me how I can adjust my webcam settings in Gyachi?:D

The brightness goes far too bright, and there are no brightness controls. I just turn off any auto adjust settings in  Kopete, works perfectly.

BTW, I noticed your display image has a Philippine flag on it. Mabuhay kabayan!:)

---

### Post by punong_bisyonaryo on 2007-07-09
whoops, spoke too soon.:) found it!:)

---

### Post by loell on 2007-07-09
> **punong_bisyonaryo said:**
> 

BTW, I noticed your display image has a Philippine flag on it. Mabuhay kabayan!:)

you could just have noticed my location , then you'll know right away.. 

and yeah i knew that your pinoy too , as your forum handle implies ;)

Mabuhay din, **visionary freak**  :lolflag:

---

### Post by punong_bisyonaryo on 2007-07-10
Oo nga no, hehe!

Have you tried Kopete? For some reason, my video stream gets to the other end fine. But the only thing I'm receiving from the other end is the very start of the stream, and it stops indefinitely, like an infinite lag. Webchatting with YM users is getting so frustrating....

---

### Post by loell on 2007-07-10
> **punong_bisyonaryo said:**
> Oo nga no, hehe!

Have you tried Kopete? For some reason, my video stream gets to the other end fine. But the only thing I'm receiving from the other end is the very start of the stream, and it stops indefinitely, like an infinite lag. Webchatting with YM users is getting so frustrating....

this could be a yahoo server issue , it also lags on the official YM sometimes

---

### Post by punong_bisyonaryo on 2007-08-01
Just like to officially recommend WengoPhone 2.1. After about 2 weeks of using it with my webcam for videochat, I'd say it's pretty ok. Although once Wengo is using sound for voice communications, no other sound comes out from my laptop: firefox, totem, rhythmbox, nothing, on both the portaudio and alsa builds. I also loaded up my Wengo account with 10euros. Voice quality is great, and it's quite cheap too!

I'm hoping more people use it, and WengoPhone gets better, so that it becomes the new open standard, instead of closed, proprietary Skype.

---

