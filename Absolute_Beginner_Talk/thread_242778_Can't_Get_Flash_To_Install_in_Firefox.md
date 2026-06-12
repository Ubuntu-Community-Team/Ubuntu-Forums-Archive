---
title: "Can't Get Flash To Install in Firefox"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Olly1234 on 2006-08-24
Hey everone, I cant get flash to install in firefox, I donload the plugin, but when I run the installer in the terminal it wants to insall it to /home/olly/mozilla. When that is not the directory my mozilla file is in. However, when I try to copy and paste the plugin install into my plugin folder it says "you do not have permission". Please Help!!! Thanks

---

### Post by macogw on 2006-08-24
Well Flash 7 was the last one released.  There is no Flash 9 for Linux.  To get that to work (which you'd probably be more interested in) download the Windows version of Flash 9 and of Mozilla.  Install these with Wine so that Flash 9 is plugged int your wined Windows Mozilla.  Then run this version of Mozilla as your browser, and you'll be able to see Flash 9 stuff just like on Windows.

---

### Post by hotbrainz on 2006-08-24
Let me just suggest that you use Automatix. this will do all the esssential installs for you from easy graphical interface.
It is available at:

[Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405")

As far as the permission thing is concerned, you need to be in the root mode to do the cut - paste operation u desire.

In the terminal u will have to type
sudo

and then your password which is the same password u need for the normal login.

But if you want to do a windows- like copy paste  in the graphical interface then u need to type:

gksudo nautilus

Caution: As a root user be careful, u can change anything and so you may delete some system files and then be in trouble.


Hope this helps
Cheers

---

### Post by xpod on 2006-08-24
Can i ask a quick question regarding the above......I have the ubunto FF and i have Swiftfox......IF i were to do as above could i safely remove the version of ff already there OR would the mozilla one automatically replace it like i was just doing an upgrade???
I asked a similar question upon installing swiftfox but was advised that it would be a bad idea to uninstall FF?

I currently get flash stuff ok but ONLY some for obvious reasons?
Thank you for any pointers

---

### Post by Olly1234 on 2006-08-24
Yay, thanks :)

---

### Post by hotbrainz on 2006-08-24
Hello Xpod,

Well I did read that thread of yours where you wanted to switch to Swiftfox and all. 
Well, yes u can uninstall it and go for a fresh version. But dont forget to save your bookmarks.

The Uninsatll if i remember rite was discouraged coz firefox is a really good browser. Is that rite or my memory is in guano.

Hope this helps

---

### Post by xpod on 2006-08-24
Yeah ...thats the one....THAT thread seemed to go OFF in all directions but then they usually DO when im around....lol

The removing of FF was advised against as they reckoned it would be a problem with other things.....i could`nt tell you what though.It was`nt discouraged because it was just so good though

Im not really fussy about ANYTHING......i just like to do stuff to see how to do it, and i have come across the odd page where i get asked to install the latest flash player SO.. when in rome......:p

---

### Post by hraposo on 2006-08-24
sudo apt-get install flashplayer-mozilla

---

### Post by macogw on 2006-08-24
> **xpod said:**
> Yeah ...thats the one....THAT thread seemed to go OFF in all directions but then they usually DO when im around....lol

The removing of FF was advised against as they reckoned it would be a problem with other things.....i could`nt tell you what though.It was`nt discouraged because it was just so good though

Im not really fussy about ANYTHING......i just like to do stuff to see how to do it, and i have come across the odd page where i get asked to install the latest flash player SO.. when in rome......:p

Well the latest flash player is 9 and it's windows-only, so see my post above about running the windows mozilla on wine with flash in there because that's the only way to run flash 9 on linux

---

### Post by xpod on 2006-08-24
Cheers.....i know about "wine"....just havent ever found the need to get it 

....Mind you i had to go back to xp to edit my avatar as the gimp was just too much in the 10 mins i had:frown: 

I`ll give it a try later once i figure out my present plethora of probs...
Thanks for the advice........Did`nt i read somewhere that the flash probs will be getting fixed for the next release of ubunto(or something like that?)

---

### Post by hotbrainz on 2006-08-24
Hey Xpod,

Feel free to uninstall and let me know what happens. It will be fun i guess. If you have the time. A system crash does not seem very enticing to me :)

---

### Post by xpod on 2006-08-24
A word about "crashes"...IF it was`nt for all the "crashes" i had when first switching that pc with m.e then xp on a few months ago THEN i would`nt have learned half the stuff i have BUT WORSE...................

...I might never have found my way to FF then soon after ubunto...I`d still be "there" posting some "hyjackthis" log on some other forum or figuring what the next BSOD actually meant! 

Bill showed me the way...so i wandered down yonder road and HERE i am.

BIG UP BILL AND HIS WONKY WINDOWS......IT`ll only lead to MORE linux users.

We were going to go out and buy a nice shiny new "vista" when it was ready.
Thank god i learned quickly on some old second hand one first.
STILL going to buy "new"......JUST new hardware now though,The only "vista" i`ll have is the one out the "windows" i can see from where i sit.

SO....you see...crashes aint ALL bad...lol

---

### Post by hotbrainz on 2006-08-24
I am called "Demolition Recovery man", I get ppl coming to me every other day with crashed Windoze PCs and then i do a brain tiring recovery of documents. To top this, the systems are sometimes in chinese. But when finished i give my mates a CD of Ubuntu and I have got 2 new converts now. 

So crashes in Windoze are good...u seee.

---

### Post by xpod on 2006-08-24
Some of the "english" stuff is still chinese to me but i have a rare old time doing the traslating.
Less than half a year(ish)at this and NOW im the one who goes and removes ALL the family and friend`s lovely new toolbars they dont know how they got(mmmmm)and  tidys up all the needless services and processes that slow their machines down.
My ubunto iso i first got 2 weeks ago is now installed on 3 other pc`s outwith this house and the Kubunto i have on another sys as well as my xubunto cd are both on their way to south africa.

Spread the word around ......and the cd`s

EDIT:   IF it aint broken then im determined to fix it

---

