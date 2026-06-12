---
title: "Evolution and microsoft exchange server Authentication problem"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by AKG on 2007-02-28
Hi, I know there's a lot of information out there on using Evolution for exchange server mail, but I still seem to be having problems at the authentication stage of the account setup.

in account setup you enter [domain\user_name] for your user name, and the appropriate URL for OWA URL.  But I know for a fact that my company's OWA URL (webmail.panasonic.com) asks for my entire email address before giving me a pop-up to enter my user name and password.    Could this be why my authentication fails?  Do other company's OWA URL ask for the email address first also?  

Any help is much appreciated. :)

---

### Post by mnk0 on 2007-04-02
Hmm,. i had initially setup my evolution for MS Exchange about 3 months ago, and had it working fine, i used  "domain\username" to connect.

Suddenly stopped working. anyone run into a similar problem?


--
Omar Samad

---

### Post by imthemp3king on 2007-04-03
I am trying to setup Evolution and I am getting thing as the original poster.  I can enter in the OWA URL and my domain\username, I click the authenticate button and enter my password.  It will close the box and but I will not have the option of clicking Next as it is greyed out.  This is a fresh install of Edgy with all updates that were available after installation from the default repos have been installed.

---

### Post by cjl2301 on 2007-04-11
> **imthemp3king said:**
> I am trying to setup Evolution and I am getting thing as the original poster.  I can enter in the OWA URL and my domain\username, I click the authenticate button and enter my password.  It will close the box and but I will not have the option of clicking Next as it is greyed out.  This is a fresh install of Edgy with all updates that were available after installation from the default repos have been installed.

All I can tell you is that I'm having the exact same problem and have not found any answers yet...

---

### Post by RadioEd on 2007-05-06
I'm having the same problem too.  I was accessing MS Exchange via webmail in a previous version.  Bummer, I like Evolution, but this problem is annoying.

---

### Post by mynk on 2008-04-29
Me facing the same issue. My colleague got it working on Thunderbird. We have seen this problem on Gutsy and Hardy. Kindly advise.

Thx,
Mynk

---

### Post by redwing629 on 2008-04-29
YES, recently (April 26, 2008) I installed the usual patches/updates using Ubuntu 7.10 and then all of a sudden I could not connect to my Exchange server using evolution. I also upgraded to version 8.04 and it still will not connect to OWA. I asked the administrators about this and they said nothing has changed with the Exchange server. To test this theory that a recent set of patches/updates caused the problem I reinstalled version 7.10 without updating and voila it works. So what was pushed out to us recently that affected the exchange connector?

Joe

=========


> **mnk0 said:**
> Hmm,. i had initially setup my evolution for MS Exchange about 3 months ago, and had it working fine, i used  "domain\username" to connect.

Suddenly stopped working. anyone run into a similar problem?


--
Omar Samad

---

### Post by pjones0404 on 2008-04-29
i am curious about this as well. I use an exchange server at work and i am unable to set it up in evolution. 

i thought i read somewhere that it is an issue w/ exchange 2007. Do you guys know if you are running 2007 or not?

 i would love to get this working as i hate the webmail interface.

---

### Post by someonestolecc on 2008-05-03
I have a very similar set up as our exchange OWA is outsourced.

I have tried with 2 different computers with hardy and get different errors on both...

I also just use my email address to login, never had to type in a domain before on OWA using a browser (I don't even know what my domain would be since the exchange server is out sourced).

I login to [https://blahblah/owa/auth/logon.aspx](https://blahblah/owa/auth/logon.aspx)

On my home pc when I use that in the Evolution Setup Assistant and click authenticate it comes back with the error:

The Exchange server is not compatible with Exchange Connector.
The server is running Exchange 5.5 Exchange Connector supports Microsoft Exchange 2000 and 2003 only.

I have no idea what that means since it's not grammatically correct... :( 

When I try on my work pc it just says authentication failure.

I also noticed it asks me for my password twice.. first time for my email address, second one for my username. Does everyone else get this too?

Can't switch my work desktop to ubuntu permanently till I can run everything I need :(


edit:

I tried [https://blahblah/exchange/](https://blahblah/exchange/) on my home pc and and now back to the authentication error. Oh well at least the inconsistency between pcs was caused by me. have to be thankful for little things :)

---

### Post by pvanos on 2008-05-09
I had same problem : after Ubuntu upgrade, no more connection using Exchange account. After removal of the Exchange account, restarting machine, and adding Exchange account, I couldn't get past the [Authenticate] screen.

With no Exchange account present in Evolution, using Konqueror I went to 
***/usr/bin/exchange-connector-setup-2.22***   and executed it.
(At the time I used it to originally create the Exchange account, it was version 2.10)

So a wizard was opening, enter the requested info (format see below), and tadaaa...

OWA URL   :  [https://mailserver.company.com/exchange](https://mailserver.company.com/exchange)
user name :  mailaccount     (without the @domain part !)
password  :  blahdiblah

Then the next screen asks for your Global Catalog Server. With Windows Active Directory the ip-address of your Domain Controller.

So basically it looks like adding/modifying an Exchange account from within Evolution doesn't work here, and it is better to use the exchange-connector-setup tool V2.22 instead.

Hope this helps...

---

### Post by sequethin on 2008-05-12
I just tried using /usr/bin/exchange-connector-setup-2.22 and it still tells me that the URL I provided is for an Exchange 5.5 server. It's exchange 2007 though, that's for sure.

---

### Post by gmstalk on 2008-06-02
I am also stuck with this. When I user the OWA address in firefox for the web interface, it work fine. I cannot auth on our new 2007 server through evolution. It used to work, but now it does not.

It looks like this is pretty common. Someone had success with adding entries in the /etc/hosts file. I will see what that does. This is annoying.

---

### Post by tshrinivasan on 2008-06-03
Me too getting the error 

"The server is running Exchange 5.5. Exchange Connector   supports Microsoft Exchange 2000 and 2003 only."

We run 2007 server.

Any help?

---

### Post by mikebunt on 2008-06-03
> **RadioEd said:**
> I'm having the same problem too.  I was accessing MS Exchange via webmail in a previous version.  Bummer, I like Evolution, but this problem is annoying.

I noticed that Hardy has the exchange plugin excluded from Evolution (compared to Gutsys include), check for that plugin. That aside, have you checked auth. criteria? What Ubuntu are you running?

---

### Post by stix213 on 2008-07-01
The problem where Evolution can't connect to Exchange 2007 is a known issue.  Hopefully support for Exchange 2007 is added soon.  

Bug # 206346
[https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/206346](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/206346)

---

