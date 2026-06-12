---
title: "Chat - Need an all in one solution! :)"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-10-11
Hi there,

I need something that can chat, send files, chat voice(VOIP) and webcam from Linux To Windows. I have tried Ekiga and the quality was really bad. I'm currently using googletalk on Kopete(which supports my webcam better than skype in windows). But I can't transfer files or use my web cam. I use Skype in linux for the casual chat but I need to reboot into windows to use my webcam!

So, what account and client do I need to get to be able to have a Fully functional chat system in place - and it needs to be free - working on a student budget here! :P

Thanks for any help,

Rudolf

---

### Post by aktiwers on 2007-10-11
You could have a look at GYachi yahoo client:
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)

I think it offers everything you need, from Webcam, Chat voice, normal chat and I think it supports sending files too! :) 

Havent used it much, so I cant really answer many questions, but give it a go :)

Edit:
Oh yeah you problerbly need libjasper to install the deb from there page. I found one here
[http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-1.701-1_1](http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-1.701-1_1)

As I couldnt not find one in the repo's.

Good luck

---

### Post by loell on 2007-10-11
what you really need to do is account and application consolidation, you can mix two accounts and two apps to achieve what you want.

for example use amsn for webcam and skype for voice and file transfer , gyachi for (webcam and file transfer) and gizmo for voice, which ever fits you.

---

### Post by RudolfMDLT on 2007-10-11
Thanks guys!

GYachi seems like it will do the job! Have had me some trouble trying to compile it but in the end I got it launched! :)

But how does this thing work! :confused:

It looks more like a chatroom client than a chat client? or what? And how do I login? I have given it a Yahoo login(Does this need an @yahoo.com?), but it doesn't ask for a password. when I click connect it asks for a password -AND also a chat room and server. 

I'm already an hour behind and I'm writing 2 tests today so I need to get studying(It's just after 5 in the morning!) :) Somebody mind explaining quickly how this thing works!? Anyway, I need to be able to chat with some one, only 1 person, in private that runs windows.

Sorry if I'm being noobish! 

Thanks a lot for the help so far! :)

Rudolf

---

### Post by loell on 2007-10-12
you don't need to put @yahoo.com, just input your yahoo username and password, check the no chatroom checkbox, choose one of yahoo's server - preferrably one of the first three servers on the list, then click login.

oh since you're compiling it yourself, just make sure you got it from cvs, not the old source.

in any case you can use this [deb package built from cvs]("http://www.mediafire.com/?0edr0enrodg")

---

### Post by AgentZ86 on 2007-10-13
> **RudolfMDLT said:**
> Hi there,

I need something that can chat, send files, chat voice(VOIP) and webcam from Linux To Windows. I have tried Ekiga and the quality was really bad. I'm currently using googletalk on Kopete(which supports my webcam better than skype in windows). But I can't transfer files or use my web cam. I use Skype in linux for the casual chat but I need to reboot into windows to use my webcam!

So, what account and client do I need to get to be able to have a Fully functional chat system in place - and it needs to be free - working on a student budget here! :P

Thanks for any help,

Rudolf

Well, I'm tossing this around some too, what I've been doing for now is using an app called userplane, it's free, and they have a few nice things like flash webcam/voice vid and chat which does not use any downloads.

I signed up and basically gave out my link
[www.iclbiz.com](www.iclbiz.com) it's my room I created with userplane app, [www.userplane](www.userplane), but anyhow you can play with that and see if it works for you for voice and video, FYI no pesky downloads needed thats one good thing.

I've been toying around with it, and cam works well, but my usb audio in linux is not recognized cause it's built onto the cam. It does work on the other linux apps, but there is just no pulldown to select the usb mic.So I have to use a regular mic plugged into the sound card or line in on the sound card.

Anyhow I'll have to fool with it some more to get my webcam mic working on userplane probably just some setting someplace on my end.

And for your transfer of files,you can use the default app in Ubunutu called Pidgin and works quit well for the chat and file transfers on all the networks I believer msn,yahoo,aol etc., but you can use the userplane for vidoe chat, 
However it's not compatible with the other systems for voice/video chat like msn,yahoo, etc. basically it's in it's own system which is a sort of setback, but it does work and you can just send the link to your chat buddy or host the script on your webpage and just send people there like I am doing now to live chat voice and video etc. 

Thats all I know about for now. I'm going to keep kicking this around myself and post back again if I find anything better.

I hope this helps some.

---

### Post by RudolfMDLT on 2007-10-15
I have a hybrid system working now:

Using skype and a Kopete on Yahoo account to Voip and WebCam. Waiting for a friend to download OpenWengo. I have had a look and I think OpenWengo will do the trick!

If anybody needs help getting there webcam to work in Kopete, download camstream and use camstream to first prep the Webcam otherwise I have found Kopete will complain a lot!

Cheers,


Rudolf

---

### Post by RudolfMDLT on 2007-10-15
Just tested WengoPhone - it's a bit slow but it's damn crystal clear! and the webcam works out of the box! The file transfer is also ,miles faster than skype's. I have found though that it doesn't like to share the soundcard with amarok or any other players. :)

Not the perfect solution yet - but damn nice an open source alternative to skype!

---

### Post by AgentZ86 on 2007-12-27
Yes does work nice, however I just wish it could live AV (audio/video) with other services like msn,yahoo,aol etc. but it does work nice, if wengo ever gets that figured out I think that is all anyone would ever need or want.

They also have a live conferencing thing you can use online no downloads at all and it's free for personal use pretty darn cool too.

---

### Post by ayllu on 2008-01-01
I think the best solution until have a software for MSN and yahoo voice chat is MSN messanger in XP in a virtual box. I use it and is work fine. I Disconect my pidgin and start my virtual box to do some calls.

---

### Post by simplejordon on 2008-01-30
The best solution without any frills is of courrse Rhubcom's appliance ( see my sign ) . It delivers advanced web conferencing software for PC and Mac in a secured appliance. Here you can share your desktops and do many things. You can chat or voice with users. I am using it over an year and that's I found pretty good for secure solutions. For general purposes ...you can go ahead with as the guys said above ..I mean MSN or Yahoo voice chat is still going ok.

---

