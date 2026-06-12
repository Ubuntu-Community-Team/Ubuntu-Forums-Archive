---
title: "Total New trying to access MSN dial up"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by jimbalaya on 2006-04-21
Any help is greatly appreciated!

I am new to Linux and trying to get online using my MSN:twisted:  dial-up account, I have a URS 56K serial modem. I used the networking utility to set up my account. Entered all the info that was asked and still cannot connect. 
Everytime the modem dials out the operators voice comes on saying please hang up and dial again.

Is there any unique problem associated with dialing in to the Evil Empire?:confused: 

Again I am a total newb! I am probably missing something staring me right in the face.

 I have read through the forums and found the Ubuntu community to be incredibly helpful:D

---

### Post by Mustard on 2006-04-21
> I have read through the forums and found the Ubuntu community to be incredibly helpful

While this can be true, a lot depends on whether someone knows the answer. :)

You might try looking over this guide to see if you can have more succes setting up your dialup connection (the relevant information for you would be towards the bottom of the page, since you're not using a winmodem)..
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

I started using the Networking gui to set up my dialup connection, but found it wasn't to my liking.  I preferred using pppconfig, which gave me more control over the connection configuration.

---

### Post by jimbalaya on 2006-04-21
I will look throught the how to's and give it a try.

Hope somebody is in or has been in the same predicament as me](*,) 

Thanks for your Mustard!

---

### Post by jimbalaya on 2006-04-26
No such luck getting connected yet.

Here is my log
local host chat [11567]: expect (OK)
                               : ATZ M^M^
                               :OK
                               : -- got it
                               : send [ATDT#######^M]
                               :expect (connect)
                               :^M
                               :alarm
                               :failed
                               :connect scrip failed
                               :exit

Any thoughts anybody?

---

### Post by Mustard on 2006-04-26
Are you using PAP or CHAP to connect?

---

### Post by jimbalaya on 2006-04-26
Thanks alot for the help!

Using PAP

---

### Post by Mustard on 2006-04-26
[QUOTE=jimbalaya]Thanks alot for the help!

Using PAP[/QUOTE]

So does that mean your using PAP now and its working, or does it mean you have been using PAP in the past its not working?

If its still not working I would try CHAP.

---

### Post by steve.horsley on 2006-04-27
If the operator's voice comes on and says to dial again, you are not even reaching the right number. Make sure you have the right number configured, including any prefix. Also, try putting some pauses in the dial string in various places to slow down the dialling speed. I think a dash "-" between numbers might do this, but it's been a long time and I might be wrong there.

---

### Post by Astinsan on 2006-04-27
You may be long distance but in the same area code. try adding a area code. Don't forget to put a 1 before the start (if your in the states that is).

---

### Post by jimbalaya on 2006-05-05
Found what the problem was, I am writing from Ubuntu and lovin it.

Found one of the answers after a google search took me to a Gentoo users forum, anybody trying to dial in to a MSN account has to put MSN/ in front of their account name.

A stupid little thing from the evil empire to deal with. But it was fun trying to get help from the MSN technical support people. After being transfered a couple times finaly got to a technician who said it wasn't possible.

By the way I am using a PAP connection

---

### Post by Mustard on 2006-05-06
That's a pretty obscure piece of information that I am sure many people will be thankful you posted in this thread. :)  

Well done, btw, on finding the answer.

---

