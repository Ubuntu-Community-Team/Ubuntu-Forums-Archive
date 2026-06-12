---
title: "Strange noise problem caused by mouse movement."
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-09-26
O.K. Don't laugh!!!

I have a LOGITECH S 510 Cordeless Keyboard connected to my PC which is running Ubuntu 7.04.

I have a dual speaker system mounted within the 5.25 internal bay. The specs are as follows:


FEATURES- Stereo Internal PC Drive Bay Speaker with 10W Amp- Black       
Internal speaker PC speaker system is the perfect solution for       
companies and schools who want multimedia capabilities for their 
PCs without the clutter of external satellite speakers.  The unit 
mounts in a 5.25 PC drive bay. It includes cables and a special 
internal to external backplate that allows an external connection to 
the sound card.  A swivel mechanism allows the sound to be directed 
to the left or right. 

 * 10W built-in stereo music amplifier.                                     
 * Fits exactly into 5.25  drive bays.                                      
 * Speaker angle is adjustable 15 degrees Left or Right.                    
 * Front panel volume control and headphone jack.                           
 * Power indicator LED.                                                     
 * Includes PC backplate with wire to connect to sound card's external outpu
   jack.                                                                    
 * Uses internal PC power supply (cable included).                          
   startech  startech  -

The exact model is on Ebay at:
[http://cgi.ebay.com/Startech-com-SPEAKERINTB-Internal-5-25-Bay-Speaker_W0QQitemZ180048111247QQihZ008QQcategoryZ31534QQrdZ1QQssPageNameZWD1VQQcmdZViewItem](http://cgi.ebay.com/Startech-com-SPEAKERINTB-Internal-5-25-Bay-Speaker_W0QQitemZ180048111247QQihZ008QQcategoryZ31534QQrdZ1QQssPageNameZWD1VQQcmdZViewItem) 

HERE IS THE PROBLEM.......

Everytime I move the MOUSE a sort of "scretching" sound come from the speakers each and everytime the mouse moves.....

I have no idea what the cause is but trust somebody "Clever" out there does!!!!

Thanks for the insight into this most unusual problem and annoying sound....

---

### Post by Skerit on 2007-09-26
Lol, this problem is similar to the ones I used to have in Windows.

Well, it wasn't a problem then, they probably considered it a feature, sometimes when the computer would lock up, the mouse would trigger the internal speaker and make little tick noises...

However, that's not very relevant here, I'm not quite sure what would cause it ...

I reckon it to be some kind of frequency thing, on some old computers my speakers would emit a very soft but high frequency pitch whenever I would move the mouse. You had to listen *very* good, but it was there. No idea how to fix it, though.

I would take a guess and say something about irq and dma channels, but I haven't touched any of those settings on an after-2000 computer in years...

Basically, I'm here for your support! \\:D/
Sorry I couldn't offer better help ...

---

### Post by CaptainInsaneO on 2007-09-26
I have the same sort of problem but it's not coming from the speakers, it comes from the motherboard itself (there's no fix for my problem, it's simply the power running through the lines, my mouse runs at 1000Hz and the res is 2000dpi :guitar:).

It sounds maybe like a grounding problem, or power from your mouse is bleeding into your speakers. Have you tried shutting the speakers off? If it still does it, you're either getting bleed-over or your speakers are just catching the interference from your mouse. You didn't say whether your mouse was also wireless, but if it is, you are looking at an interference problem. Same thing happens with many cell phones.

---

### Post by lentomies on 2007-09-26
Thanks for the "tips" guys.

The S510 includes a mouse as its a bundled deal the customer buys. I guess it makes sense to sell things that way?

I turned off the speakers and still hear that awful scratching noise..... So I pulled the plug for a while.... Relief.....

If I wanted to play around with the irq and dma channels what am I looking to do exactly?

---

### Post by kyphi on 2007-09-27
There are too many radio devices too close together and they are causing interference.

So, if you have a modem with WLAN enabled, cordless mouse, cordless keyboard and perhaps a cordless phone as well as built in speakers with magnets too close together you are asking for trouble.

BTW lentomies, is the issue with the calendar view resolved?

---

### Post by Mr.Beast on 2007-09-27
I would intend to agree with Kyphi, multiple devices using the same frequency in the same location.  
Good news though, normally you don't have to move them too far away from each other to get the problem to dissappear.

I assume that you keyboard and mouse receiver are USB.  simply get a USB extension cable and move it away from it's current surroundings. 

got to be worth a shot.

---

### Post by lentomies on 2007-09-28
Yes my Calendar view is resolved... Thanks for asking!

I actually don't have too many devices near those internal speakers....... The device that talks to the wireless mouse and keyboard is maybe 2 feet from them as compared to 4 feet from the tower...

Thanks for the suggestions nonetheless

---

### Post by kyphi on 2007-09-29
I did not mean that your devices are too close to your inbuilt speakers but that the magnets in the loudspeakers constitute an electric field as does the transformer in your power supply as well as any other transformer for your monitor, your printer, your modem, your scanner and so on.

It would be great if component manufacturers could settle on a universal power supply so that everything could be plugged into the same transformer but then there is current draw that has to be regulated.

From the equipment you described, all those wireless operated pieces rely on radio frequencies to be able to communicate with each other.  There is sure to be some cross talk.

Try a wired mouse and wired keyboard - it might solve the problem.

Off topic: Just as well that I am old enough to remember how long feet are.

---

### Post by BummerCZ on 2007-10-01
I had this problem under Windows and also under Ubuntu. It's always the same. You can solve it by muting the sound output from you CD drive. Try it. *thumbs up*

---

### Post by Esclepiodoto on 2007-10-01
I have a Duron, I don't know right now what's his speed. Ask for the rest of the data if someone is interested.

I installed Ubuntu, and I at first did not hear the noise you are talking about (I think it is the same noise). I recently installed XMMS, and this is, I think, when noise on my computer started on.

I read the last post, in which BummerCZ suggested to mute the CD output. However, I started to mute everything, and I found that muting  the speaker stopped this noise.

Cheers.

Esclepiodoto

---

### Post by guardiansps on 2007-10-24
i tried this and it worked for me. maybe it will be usefull for all of you too.
simply do this...
go to volume options and click advanced on the mic volume, below there sould be two boxes one that says "mic boost" and another that says "stereo mic".
uncheck the "mic boost" box and if that has result try checking the other box.:)

---

### Post by arpad9 on 2008-03-18
No, no, no, no.  Honestly, all worthy guesses.  But, if his problem is anything like mine (and I don't have a solution to this yet), I think you're all wrong.

When I move my mouse, it make sounds *sometimes*.  It all depends on what I'm doing.  If I'm moving across the desktop, almost no sound.  BUT, if I'm scrolling a web page, LOTS of sound. 

Hmm. I just tried not touching my mouse at all and just rotating my cube.  Same sound.  Not mouse related.   Hmmm.  Video card interference on the motherboard??  Weird.

Any clues?

Ha, here's another funny thing.  If I turn my volume all the way up and do nothing, I can hear a "thump, thump, thump, thump."  Very faint.  IT'S ALIVE!!!

Really I don't care about the above but I am trying to figure out why the heck there's a click in the Skype that I broadcast.

---

