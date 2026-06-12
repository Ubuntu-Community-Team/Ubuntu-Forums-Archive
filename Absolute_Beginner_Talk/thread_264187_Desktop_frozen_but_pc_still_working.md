---
title: "Desktop frozen but pc still working???"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-09-24
Well,My own problem for the day now

[ATTACH]16259[/ATTACH]

MY whole desktop has froze for some reason.The panel at the top has been removed but as you can see is still there with nothing usable on it.
The same with the desklets and down to the bottom panel which allowed me to at least add a new panel to get a menu up on just to get back online with.

I have even rebooted but the problem persists.
I had just rebooted to swap my modem usb wire over to ethernet wire.
I use the usb to stick in our kubunto but never had a problem like this before.
Cant do nothing to get rid of or use any of the stuff on that desktop other than the new panel with menu you can see over the top of thebottom panel.

Its` only a clean install as of yesterday and had all updates etc etc.

Please dont tell me i need to re-install again...lol:shock:

EDIT:strangely that "home" desklet used to be orange but had went gray this morning prior to this so mabey its dodgy desklets????
DOnt know what to do though

---

### Post by bulldog on 2006-09-24
This is to complex for me,can't help you.

Advice: do a fresh install:D

---

### Post by xpod on 2006-09-24
IM going to set my 3 legged staff on you you bulldog you...lol
IM going back to my M.E if you dont fix this and fix this now!!!!!

I`ll be down the pub.........give me a shout when it`s DONE!!!!

EDIT...LOL;)

EDI"....OPPS,Forgot i dont drink since moving south

---

### Post by chrisfay on 2006-09-24
> I`ll be down the pub.........give me a shout when it`s DONE!!!!

Have you resorted to fabricating problems for an excuse to booze...[-X

---

### Post by bulldog on 2006-09-24
I should begin to remove things that don't work proper.

Look in your sessions menu and untick the last box in tab one.
Same place but tab 3 remove your desklets and other useless programs,I'm sure you have a lot of them :D 

Then ctrl -alt- backspace and login again and see what happens.

[bring me a beer when you come back from the pub]

---

### Post by bollix47 on 2006-09-24
Since it might be difficult to get into sessions menu with a frozen desktop you may want to try rebooting into recovery mode.

Login

sudo apt-get remove gdesklets

reboot and see if problem disappears

---

### Post by bulldog on 2006-09-24
> **bollix47 said:**
> Since it might be difficult to get into sessions menu with a frozen desktop you may want to try rebooting into recovery mode.

Login

sudo apt-get -remove gdesklets

reboot and see if problem disappears

Well you have to know a little about XPOD,he can do anything :razz: 
He has is own technician in tha house so don't worry,she'll fix this.

---

### Post by bodhi.zazen on 2006-09-24
xpod, the problem is that is one ugly desktop. :(


I like mine better. :)

---

### Post by bulldog on 2006-09-24
> **bodhi.zazen said:**
> xpod, the problem is that is one ugly desktop. :(


I like mine better. :)

That will hurt him deeply,but you're right,it's ugly.:D

---

### Post by xpod on 2006-09-24
As i said the whole thing is froze but i was able to somehow get a new panel added over the top of the frozen one alreday there..and then a new menu.

I just could`nt see it had a "system menu" in the mess thats there as well as the "apps" menu

Anyway the last box is already unchecked in the first tab and in the "startup" tab all i got in there is...."Update notifier,Gnome-power-manager and Gnome-volume-manager --sm-disable...

I presume the "sessions" thing in "preferences" is what you meant??..

Unfortunately "Kassi" is off to nan`s for sunday dinner so im stuck with no one year olds to help this time

EDIT: i`ve only installed "automatix" and the "desklets" things but the desklets did`nt have the daemon set to start at bootup

---

### Post by xpod on 2006-09-24
i was waiting on that irish contingent spoiling my fun:rolleyes:

EDIT:...i seen your desktop and i prefer the real thing......only trouble is she keeps spitting brats at me

---

### Post by bulldog on 2006-09-24
EDIT: i`ve only installed "automatix" and the "desklets" things but the desklets did`nt have the daemon set to start at bootup

Try to setup the daemon,but why are they loaded when the daemon isn't running and the last box in the first tab of your sessions menu is unticked?
Beats me,they shouldn't been loaded in the first place.

I'm holding to my first advice:Reinstall..........your box is really messed up beyound repair:D

---

### Post by bodhi.zazen on 2006-09-24
> **xpod said:**
> i was waiting on that irish contingent spoiling my fun:rolleyes:

EDIT:...i seen your desktop and i prefer the real thing......only trouble is she keeps spitting brats at me

That is my wife... :)

Just kidding, my wife keeps spitting brats at me as well. I got's 3 now.

---

### Post by xpod on 2006-09-24
Sorry i forgot to mention that if i start the desklets once ubu is up and running thats how they are on show.
If i remember correctly i had some offer of a daemon being set up but as i was`nt a 100% sure what it actually was........OK OK.DONT LAUGH:D

---

### Post by bulldog on 2006-09-24
Well if you logoff and back in without your precious desklets,is everything messed up again?

Then we can asume the desklets aren't the one we're looking for.

You should have done something to cause this.
I'm going to ask you to think deeply,yes it's hard,but you must try,what did you do prior of this mess.

---

### Post by xpod on 2006-09-24
ALL i have done my friend was pull out my modem usb from it`s port on the Ubu
pc and then use on the Kubunto next to it.

When i was finished using the broadband on that pc i switched off my Ubunto and modem and used the "ethernet" wire for it this time....when i rebooted it was all as it is......Hard to belive i aint done nothing i know:D ,BUT

You should know by now that i dont NEED to do anything to have any of our cranky  pc`s take hissy fits....lol..

I`ll reboot again but i reckon it`ll be the same......:D

---

### Post by bulldog on 2006-09-24
Is it something to do with your internet connection?

It might be your eth0 is changed to something else and you need manually alter this in your administration --> Network.

If you don't know what you're doing,why are you doing it in the first place?:D

---

### Post by xpod on 2006-09-24
Nope mate ,I think our irish friend was right all along,It just did`nt like the bloody desktop background as you can see from the reboot...lol

[ATTACH]16265[/ATTACH]

Ive swapped my internet back and forth between pc`s and usb or ethernet fine up till now if that is the case....I suppose there was`nt nothing else happening so it dosent leave much else it can be eh??

I am going to wire them all up to a network once we move house next year but it`s not been worth the bother just now

---

### Post by bulldog on 2006-09-24
Did you install any themes what can cause this trouble?

Can you change your theme at all I wonder,if so give it a try.

Is there something overheating inside your PC?

Otherwise I can't explain this,besides the very ugly desktop which now removed itself in shame.:D

---

### Post by bodhi.zazen on 2006-09-24
Banned by your own box LOL :lol:

Perhaps your wife installed some kind of taste monitor daemon on your box.

---

### Post by xpod on 2006-09-24
All fixed again mate....Well,i hope[-o< 
I had already rebooted prior to that one and ended up at a prompt for logon on the same screen as all the bootup info that scrolls by.
Logged in there but all i got was the usual username prompt from there so as i was`nt too sure what to punch in i rebooted again and it all came on fine.........albeit without my crappy desktop:D 
Anyway,tell me that one aint cool......lol

[ATTACH]16266[/ATTACH]

---

### Post by bodhi.zazen on 2006-09-24
Bahh..

There is hope for you yet.

---

### Post by bulldog on 2006-09-24
> **xpod said:**
> All fixed again mate....Well,i hope[-o< 
I had already rebooted prior to that one and ended up at a prompt for logon on the same screen as all the bootup info that scrolls by.
Logged in there but all i got was the usual username prompt from there so as i was`nt too sure what to punch in i rebooted again and it all came on fine.........albeit without my crappy desktop:D 
Anyway,tell me that one aint cool......lol

[ATTACH]16266[/ATTACH]

Well...............uhmmm...yeah very..........uuuuh....nice?

There is a pack of nice backgrounds in the art-work forum.
Take a look and choose a decent background.

I knew though,with our advice and very skilled talents,we get the solution to your probs.

One advice at least one to concider,**don't touch anything again,without your technician to aprove your actions**

---

### Post by bodhi.zazen on 2006-09-24
Perhaps this is why the "big guns" never talk to us anymore.

---

### Post by bodhi.zazen on 2006-09-24
They're behind you....

---

### Post by xpod on 2006-09-24
Sorry about that ...some "other" child was wetting his knickers elsewhere
and i was a bit pre-occupied.

So you dont approve of a bloody penguin now either...i think thats  terrible  to slag off your OS`s mascot like that.....Im going to be reporting this thread if it keeps up..

You could`nt JUST send me a good desktop could you????....GO ON,it`s ALL the rage at the moment!!!after all your stupid OS has borke my computer SOOOOOOO many times!!!:biggrin: :-({|= 

OH NO....IT dosent even feel right TRYING an attitude like THAT...LOL

Im off to do the rest MYSELF now........LOL
Good stuff guy`s....Sorry about the A**holes out there

---

