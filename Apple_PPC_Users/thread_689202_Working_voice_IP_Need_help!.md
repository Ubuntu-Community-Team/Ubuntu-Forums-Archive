---
title: "Working voice IP? Need help!"
date: 2008-02-06
forum: Apple PPC Users
---

### Post by khelben1979 on 2008-02-06
Hello!

Is there anywhere where I can get a Skype version for my ppc platform? 

Or any other program so that I can communicate with other people through voice IP? I have a sennheiser USB headset which work great on both of my PC and my mac.

My brother is running the latest version of MacOS X and for me it would be nice to able to get voice IP to work as soon as possible, My PC is currently down for repairs, something is wrong with it, probably the powersupply. :(

---

### Post by oswaldkelso on 2008-02-06
> **khelben1979 said:**
> Hello!

Is there anywhere where I can get a Skype version for my ppc platform? 

Or any other program so that I can communicate with other people through voice IP? I have a sennheiser USB headset which work great on both of my PC and my mac.

My brother is running the latest version of MacOS X and for me it would be nice to able to get voice IP to work as soon as possible, My PC is currently down for repairs, something is wrong with it, probably the powersupply. :(

Not skype but [gizmo]("http://www.gizmoproject.com/") works on both osx and ppc linux. It works using  ekiga or twinkle etc. You may need a windows or osx machine to create your account, I already had a gizmo account from osx.  If you scroll through my debian how to at the bottom of the page you'll see how to set it up in the my customizations bit. 
You may try [wengo phone]("http://www.openwengo.org/") also but as long as the person on osx or windows is using sip and not a closed protocol like skype you should be able to set up any client. Ekiga asks you if you want to register with a provider they offer you as you set it up.  I have no experiance with them.

---

### Post by khelben1979 on 2008-02-06
Interesting!

Where can I find the Gizmo ppc package? Couldn't find it on the homepage.

---

### Post by oswaldkelso on 2008-02-06
> **khelben1979 said:**
> Interesting!

Where can I find the Gizmo ppc package? Couldn't find it on the homepage.

Sorry I was not clear enough you don't need gizmo, you just need a gizmo account to get a sip account(There are lots of sip providers all offering different deals but most have free voip calls pc to pc. but they charge differing rates for pc to phone phone to pc etc) You can use any Linux package/application that supports sip.
 I just suggested gizmo and wengo phone as there are osx applications your brother/friend could install. You can use ekiga, twinkle, or any other linux  sip package /application  to communicate with gizmo or wengo phone. 

The important thing is it supports sip.  I use gizmo as my ex-girl friend has osx and has gizmo. But I use my gizmo account with ekiga on ppc. if you think of it as the sip provider is the phone company and the application you use is your make of phone, as long as your on the same network (sip) your pretty much good to go.

---

### Post by khelben1979 on 2008-02-07
Does this mean that **I must** have a SIP account?

In Debian Etch I've noticed that Ekiga is part of the distribution, but I don't like to pay for a SIP account I was hoping to be able to use Skype on this computer.

Is Skype a hopeless case on this computer platform?

---

### Post by oswaldkelso on 2008-02-07
> **khelben1979 said:**
> Does this mean that **I must** have a SIP account?

In Debian Etch I've noticed that Ekiga is part of the distribution, but I don't like to pay for a SIP account I was hoping to be able to use Skype on this computer.

Is Skype a hopeless case on this computer platform?

Ekiga is part of the gnome desktop that happens to be the "default" debian desktop I'm not sure i'd say it was part of the distribution per say. You only pay to make calls to phones or mobiles with sip accounts no need to pay if you only want to use sip between pc's, when you register you get a "number". No skype for ppc. If your desperate for it you could try running it in osx with [MOL]("http://mac-on-linux.sourceforge.net/") its in the repositories but I have no idea if it would work or how well.

---

### Post by khelben1979 on 2008-02-08
I'm not desperate in using the Skype on the PPC.

I will try out Ekiga and I'm hoping to get it to work against a MacOS X system when IChat is being used. It sounds positive that I don't need an SIP account to able to use Ekiga, sounds positive.

---

### Post by oswaldkelso on 2008-02-08
> **khelben1979 said:**
> I'm not desperate in using the Skype on the PPC.

I will try out Ekiga and I'm hoping to get it to work against a MacOS X system when IChat is being used. It sounds positive that I don't need an SIP account to able to use Ekiga, sounds positive.

You DO need a sip account to get a number its free. If you choose to buy PHONE credit as well, to ring friends on a land line or mobile then that's up to you.  pc to pc is free.

I'm pretty sure ichat is not sip but if I remenber right the chat may work but not phone, so your friends need a sip application for osx. gizmo or wengo-phone work on osx there maybe others?. They need to install it, You can use any sip application from the repositories.

try ekiga and see how you get on  use synaptic and search sip there are lots some may be better than others or have different features. I suggested gizmo and ekiga as I know it worked when I was running etch and my ex was on osx.

---

### Post by khelben1979 on 2008-02-08
Okay. If I can't communicate through voice from Ekiga to my brothers' system OS X, then, for the moment Ekiga doesn't really give me so much. Although, it's nice that the SIP account is a free service. This means that if someone else is running Ekiga on a Linux system I should be able to call this person for free. That is just like the Skype client works, nice!

Thanks for your advice so far. :)

---

### Post by oswaldkelso on 2008-02-09
You CAN talk to your brother with sip (voice) using ekiga but he must install a sip application on his mac. gizmo or wengo phone are the ones I know of that work on osx. 

Get your brother to down load and install gizmo and register 2 accounts one for you and one for him.  I'll tell you how to set up ekiga so you can both talk for free. 

That will give you 2 numbers (thats why we  register to get a number)

IF  your brother wants wengo phone because it has web cam support, then we'll play it by ear.

If you want to use wengo phone, twinke or some other sip application on your debian etch computer thats fine once you have a number. Some may work better than others, this is Linux after all you have the freedon to use what ever you want. But i would advise that you get ekiga up and running then play with other applications when you have a feel for things

---

