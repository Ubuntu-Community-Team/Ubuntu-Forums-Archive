---
title: "Yet Another Newbie Internet Connection Problem"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by gerryl on 2007-07-24
I just received my Dell XPS desktop system with Ubuntu v7.04, and Verizon DSL.  Verizon provided a Westell modem, model 1600 which I connected via Ethernet.  On the modem the DSL light is on, the Ethernet light blinks, and the Internet light occasionally comes on red.  Using Firefox, if I go to the modem IP address, 192.168.1.1 I see status messages: 
Your modem is not ready for Internet Access. 
Internet status – not connected
DSL link – connected
PPP status – down

But the status page correctly shows the modem model number, so there is obviously some successful communication.  If I run “sudo pppoeconf” I do not get the data entry fields described in the manuals.  Instead I get a message “Sorry – I scanned 1 interface but the Access Concentrator on your provider did not respond…”  If I run “sudo pppoe-discovery” I get “Timeout waiting for PADO packets.”
Am I doing something exceptionally dumb?  The modem is apparently a new model – could it be that Ubuntu does not yet support it?  Or might the modem be defective?  HELP!!:confused:

---

### Post by philter on 2007-07-24
Did you already have Verizon DSL installed at your home, or was this a whole brand new setup? If it is a brand new setup I'm guessing you'll probably have to call the DSL provider and talk with them to find out if you have DSL enabled on your phone lines already. Usually they package a CD that will run under Windows and it sets up your modem, but since you're not running Windows the company support will probably be able to advise you on how to proceed with the setup.

---

### Post by jnorthr on 2007-07-24
Perhaps the Dell help desk may offer some positive advice since they sold it to you. Their tech support may not yet be up to scratch but it's worth a shot.

---

### Post by gerryl on 2007-07-24
Thanks for the prompt reply.
The DSL setup is a whole new setup.  Yes, they did provide a CD for Windows or MAC installations, and yes, they did notify me that my service has been initiated (I assumed that the DSL light on the modem confirms this).  I did contact Verizon Customer "Support,"  but apparently they never heard of Linux in India, and they were of no help.

---

### Post by jnorthr on 2007-07-24
i'm just looking at the dell site now for some info. what model is your kit ?

---

### Post by gerryl on 2007-07-24
Not sure what you mean by "kit."
The processor is a Dell XPS 410N
The OS is Ubuntu 7.04
The modem verizon sent is a Westell 1600

---

### Post by jnorthr on 2007-07-24
[http://eatourbrains.blogspot.com/2006/10/cutting-cord.html](http://eatourbrains.blogspot.com/2006/10/cutting-cord.html) appears to have some bad news for verizon users. 8-P and the 'verizon status' page at: [http://netservices.verizon.net/portal/link/main/systemstatus&status_type=DSL](http://netservices.verizon.net/portal/link/main/systemstatus&status_type=DSL)
doesn't appear to be up. Are you sure their DSL service is running ?

I cannot believe that Dell would sell computer kit that does not work. But once it arrives, getting it connected to the real world is another matter. Where to start ? let me have a cup of tea and a short think on this...

---

### Post by gerryl on 2007-07-24
Thanks again.

BTW, FWIW I had a typo - the modem is a Westell Model 6100, not 1600.

---

### Post by Ambimom on 2007-07-24
I have approximately the same setup....when the westell modem lights are red....

you need a new modem.  The same thing happened to me.

You do not need to use the verizon cd, btw.  All that does is load crap  onto your computer that you don't need.  As long as Verizon verified that your service is connected, all you need is the router and the modem.

Call verizon.

Word of caution though....finding someone at verizon who actually understands what you are telling them might take five or six calls.....

Eventually, you will get someone who will help you.

---

### Post by jnorthr on 2007-07-24
pls keep us advised.

you probably won't need this but just in case: [http://www.lava.net/support/Westell_6100_DSL_Modem_Installation_Guide](http://www.lava.net/support/Westell_6100_DSL_Modem_Installation_Guide)

---

### Post by hgfire on 2007-07-24
Call Verizon before anything else and ask them if you phone line has been provisioned for DSL. Nothing will happen for you until this takes place. Secondly, the provided CD that Verizion includes in your package is nothing more than a shell (software) to the internet. It's not really needed at all. Once your line is up and running, you should have direct access to the net. Lastly, do not put a line filter (that verizion provides) on the line that runs from the wall jack to the modem, it will interfer with you data access and is only meant to cut line interference to the voice communications on your telephones, not the DSL data.

---

### Post by gerryl on 2007-07-24
Thanks for all the prompt replies.
To clarify, I was notified several days ago by Verizon that my DSL service was connected and ready for use.
The DSL light on the modem is on, which I assume confirms that I have DSL service.
I did not attempt to use the Windows installation disk provided by Verizon - I just mentioned it in response to a comment that i should have received one.
I did verify that I have the latest version of pppoeconfig loaded.
I did not put a filter on the modem line, just on my phone lines.
Verizon Customer "Service" tells me they can't help me because I am using Linux, which they don't support :(
They also claim that my modem cannot be defective since the power light comes on!!!!

---

### Post by jnorthr on 2007-07-24
Don't know about your modem but mine has two green lites - one for power (yes THAT should be green) and a second lite labelled ADSL which may indicate green if your isp machine is polling your modem address. Just as a test for you i've unplugged my kit from the modem to watch the lites. After a minute my modem lite begins to wink as it is being polled by my ISP. If you power off all your kit then wait a minute then power the modem on first, then your kit, you may be able to see your modem lites wink if/when your ISP polls your modem. 

You are obviously posting on the forum so you must have a machine hooked up at the moment. Yes ? Any possibility of trying your 6100 modem on that machine just to see if you can establish a 'known' connection ?

Bon courage as the french say.

---

### Post by str8line on 2007-09-02
As a point of correction the modem that you have is probably not the Westell 1600 but the Westell 6100.  The internet light going red indicates either a drop of the PPPoE connection in the modem or the wrong password in the modem.

If you have still not created an account with Verizon (ie either calling in for manual creation or setting up the account using a Windows based pc at [http://activatemydsl.verizon.net](http://activatemydsl.verizon.net)) then that would need to be done.

---

### Post by Ambimom on 2007-09-02
Don't get me started on Verizon.....I HATE THEM!  However, they are the only game in town where I am.....

The fact that you use Linux is irrelevant as far as their connection goes....

If you have a username and password for the router...

Can you get into the router through your browser?

If you can, you can see if the PPOE is connected.  

My exceedingly painful experience with Verizon is that you must keep calling until you reach someone who actually knows what you are asking them.  When I switched phone numbers for my DSL service I had to make 15....yes 15 phone calls before I encountered someone who knew enough to flip a switch to reconnect my service.  For about three weeks, one person after another told me I did not know how to operate my computer; that it was my fault, not Verizon's that I had no DSL connection.  It seems that they had neglected some simple switch of my password.  It took about 10 seconds and voila....DSL.

You problem is probably something simple like that too.  Good luck and keep calling Verizon...over and over and over until someone understands....

---

### Post by str8line on 2007-09-05
Ambimom,

I can assure you there is no switch that can be flipped to turn on your service, DSL does not work that way.  As for you needing to call 15 times before you got someone to help, same can be said for calling nearly any frontline support number depending on the issue that you are experiencing.

---

