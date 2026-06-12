---
title: "F-spot - not running on gutsy"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by izaaa on 2007-10-31
ok, I just installed gutsy on my Vaio laptop. I was very happy about it but as expected something went wrong. [F-spot]("http://f-spot.org").

:!: when I run it in console, the reply is following:
*Can't get a connection to the dbus. Trying again... *and it's trying and trying - no success. :-s

:!: when I run it from the Panel, it doesn't run at all. all that I get is Starting F-spot and then nothing. :-s  ](*,)

:!: when I run it from the Menu (Applications/Graphics), I get very sexy fatal error:
*A null value was found where an object instance was required.*

{
the whole error message is following:
An unhandled exception was thrown: System.NullReferenceException: A null value was found where an object instance was required.

  at System.Runtime.Remoting.Proxies.RealProxy.PrivateInvoke (System.Runtime.Remoting.Proxies.RealProxy rp, IMessage msg, System.Exception& exc, System.Object[]& out_args) [0x00000] 
.NET Version: 2.0.50727.42
} 

I understand what it's trying to tell me but I don't know how to handle it. \\:D/ 
can someone please help me? [-o<  I would be very thankful!

Best regards, 
Izaaa

---

### Post by overdrank on 2007-10-31
> **izaaa said:**
> ok, I just installed gutsy on my Vaio laptop. I was very happy about it but as expected something went wrong. F-spot.

:!: when I run it in console, the reply is following:
*Can't get a connection to the dbus. Trying again... *and it's trying and trying - no success. :-s

:!: when I run it from the Panel, it doesn't run at all. all that I get is Starting F-spot and then nothing. :-s  ](*,)

:!: when I run it from the Menu (Applications/Graphics), I get very sexy fatal error:
*A null value was found where an object instance was required.*

{
the whole error message is following:
An unhandled exception was thrown: System.NullReferenceException: A null value was found where an object instance was required.

  at System.Runtime.Remoting.Proxies.RealProxy.PrivateInvoke (System.Runtime.Remoting.Proxies.RealProxy rp, IMessage msg, System.Exception& exc, System.Object[]& out_args) [0x00000] 
.NET Version: 2.0.50727.42
} 

I understand what it's trying to tell me but I don't know how to handle it. \\:D/ 
can someone please help me? [-o<  I would be very thankful!

Best regards, 
Izaaa

Hi and welcome, have you tried and remove it in synaptic manager and then reinstall. Hope this helps. Good luck!
Edit: synaptic packager manager is located under system, administration, synaptic

---

### Post by izaaa on 2007-10-31
that was my first try, yes. but that wasn't the catch. [-X

I was able to fix this by deleting my f-spot folder (rm -rf ~/.gnome2/f-spot ). fortunately I didn't have any data in the f-spot database. it's running properly now.  \\:D/

my next mission is to figure out how to get that precious ''add-on'' which allowes you to upload pcts  to picasa web album. :-k it's the reason I upgraded at first place.

---

### Post by anzevi on 2007-10-31
In Gutsy, support for Flickr and Picasa is already integrated in this version of F-spot. All you have to do is select one or more pictures from the gallery and click on File --> Export and then select the desired destination :)

Cheers

---

### Post by izaaa on 2007-11-01
tnx :popcorn:

cheers mate

---

