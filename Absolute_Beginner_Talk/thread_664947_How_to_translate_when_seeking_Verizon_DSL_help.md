---
title: "How to translate when seeking Verizon DSL help"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by jacquelinec on 2008-01-11
I need help! Verizon DSL is not set up to support Linux. I am not geeky enough (someday aspire to be) to trouble shoot without support. My DSL connection is lost. I can send Ping but 5 packets out 0 return...Is there a non-geek, English, basic HOW TO guide somewhere? 

I will have to return to this public computer tomorrow as they are closing shop! 

Thanks in advance for help.

Jackie

---

### Post by phidia on 2008-01-11
I have verizon DSL. You might want to use their support pages, however list the modem you have thorough them (you can search it also) and your system plus if you are using a router/wifi or whatever else.

Actually since all connection to the dsl modem is thru webpage you can enter setup using linux-I do.
Just give as much of the specifics as you can and what you've already tried and people will attempt to help.

---

### Post by jacquelinec on 2008-01-14
thank you for your response...i am a novice though and do not know if I have linuxI-do (?) or how to use it...all i know is my system was working one minute; not working the next and Verizon just flatly refuses to help unlsess I am using Microsoft/ IE
I got infected by security breach using that O/S and will not go back unless i find that i am unable to function in the world w/o it....

---

### Post by RRS on 2008-01-14
> **jacquelinec said:**
> .....and do not know if I have linuxI-do (?) or how to use it...
err, ahh, I believe what Phidia meant was to "use Linux", like he does.

Your modem and/or router has an IP address such as 192.168.1.1 or similar depending on make and model. Normally if you enter this in the address box of Firefox it'll open the set-up pages of the modem.

If you can provide the make/model of your modem and(if one) router someone here can probably help get you the correct IP address and any default password, etc. you may need.

> ......and Verizon just flatly refuses to help unlsess I am using Microsoft/ IE
In the meantime call Verizon back and don't tell them you're using Linux, just say your internet doesn't work.
They'll probably ask you to open IE and give you the IP to type in so they can walk you thru the set-up.  Just say "OK" and don't tell them you're opening Firefox instead ;) It's unlikely they'll ever know the difference....

> .....all i know is my system was working one minute; not working the next....
The problem could be theirs, the outside line or maybe the connection from outside into your home. they should be able to test for this from their end. I assume your phone still works ok?

If you still have problems please post back with your hardware info. and also anything else unusual that may have been happening just before you lost internet access and I'm sure someone can help.

---

### Post by jacquelinec on 2008-01-15
Thank you for the response. Absolute Beginner to me means I don't know your jargon. "like I do.." who knew that needed to be abbreviated?!

So the answer is phone is fine. Verizon claims no issue with their server. i will not open IE to walk through the Bombay Call Center script. IE is how I got infected prior to my Linux conversion! I don't want to go back to the evil empire but I lose DAYS of productivity each time there is a problem b/c I am insufficiently geeky to solve problems myself. 

Will the Canonnical paid support be a better route for me?:confused:

Our network at home (we both work from home so this is multiplying our pain!) has a Microsoft router and a westell wirespeed modem. I believe our IP address is:
192.168.2.0
Domain
169.254.0.0

I was able to get as far as requesting ping. 5 sent zero returned.

Nothing happened to prompt problems (no new installs; no updates ) just sitting there left on...went to check email before shutting down and blammo - no connection!

Thanks again.

---

### Post by dstew on 2008-01-15
I have Verizon DSL, and use Linux. To set it up, you only need to use a browser that communicates with your DSL modem's setup pages. The IP address of the modem is 192.168.1.1. I fully agree with RSS:> In the meantime call Verizon back and don't tell them you're using Linux, just say your internet doesn't work.They will take you through the steps to reconfigure your PPP over your DSL modem. Of course, you already did the usual -- turn the modem off for 20 sec, then on again. And, of course you connected directly to the Wirespeed modem, bypassing your router to make sure it is not a router problem...

---

### Post by crageye on 2008-01-15
[I][COLOR="Red"]Verizon's DSL support is horrible. First, unless you keep on saying "Operator" you won't get past the IVR. Now when you have gotten hold of one, here is what he is going to ask you to do 
- restart your modem/router
- reset your model/router
- restart your computer
- tinker with admin console
- get a new router/modem
- at last open a ticket

Few hours later, your DSL will start working on its own and you would have lost two hours of your life that you will never get back.[/COLOR][/I]
rant ends.

Router configuration is not dependent on whether you are using Linux or Windows. If you can't use linux (sometimes they do a remote control thing), get a Windows laptop and get it configured.

---

### Post by RRS on 2008-01-16
>  ......will not open IE to walk through the Bombay Call Center script.
No reason to, just tell them you are while you're actually opening Firefox in Ubuntu. That's right, lie(just a little white one though):)

> ......insufficiently geeky to solve problems myself.
No problem, that's what the forums are here for. Oh and geekiness isn't needed, many of us aren't. We just try to pass on the bits of knowledge we've have.

> .......a Microsoft router and a westell wirespeed modem.
The IP's you've posted are likely for the computer(s) themselves or one may be the router. Do you have two computers hooked to the router which is then connected to the modem? Some of your previous comments seem to indicate that but correct me if I'm wrong please.

I did a quick google search on your modem but without the model all I can be reasonable sure of is that its' IP should be 192.168.1.1

Also, since the problem could be in the router, try connecting only one computer directly to the modem and then ping 192.168.1.1 

If that works enter 192.168.1.1 in Firefox's address bar and you should get to the modems interface pages. You may be asked for login info, try "administrator" for user name and password or maybe your Verizon login. Somewhere I've got a site with default passwords and such for most modems and routers but I've gotta search my old bookmark files for it.

Since you obviously have some limitations accessing info untill this problem is solved do you have a spare cd or thumb drive? This way any possible solutions you find could be copied for more thorough study at home instead of trying to take notes by hand or decide which info will be most helpfull during a limited on-line session.

I'll dig through my jumbled mess of notes and see what else I can find for tomorrow.
Don't give up, we'll find a solution yet:popcorn:

Dohh!!  Forgot to ask you to post back with the results of:
```
ifconfig
```
Open a terminal and enter the above command and it will give info on your computers internet connection and may help with troubleshooting.

---

