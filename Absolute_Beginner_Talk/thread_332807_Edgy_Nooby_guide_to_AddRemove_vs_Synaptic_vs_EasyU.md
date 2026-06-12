---
title: "Edgy: Nooby guide to Add/Remove vs Synaptic vs EasyUbuntu vs Automatix vs...?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2007-01-06
Greetings community!

Sticking just to GUI methods (please!!) which tools should noobies use to add & remove applications?

I am aware of the 4 in the title, but there may be more.

My impression (not worth much) is that EasyUbuntu is mainly a good concentration of Multimedia applications, Synaptic is a very comprehensive tool for nearly everything (but sometimes tricky to locate what you are looking for), Add/Remove is a reduced version of Synaptic, and Automatix more-or-less overlaps with Synaptic, but not quite?

So far I have mainly used Synaptic & found it very impressive (coming from XP).

Why would I want to use any of the others?

Do they all work in harmony (recognize applications installed by 'rivals') or ignore each other, or screw each other up? (I mean if they are used one at a time, not if I tried to use them exactly at the same time...)

Do I have to remove applications with the same tool I add them?

Should noobies steer clear of any of them?

What logic guides my choice?

Thanks for your advice!

---

### Post by hyper_ch on 2007-01-06
EasyUbuntu and Automatix just do some custom installs and dependencies... like install codecs and stuff...

But all they do, you can also do with synaptic or adept (or the shell commands apt-get / aptitude).
For getting all codecs running by synaptic you will ahve to add more software repositories to your sources.list and you need to individually install them...

In the beginning I thought automatix2 is great but meanwhile I know what stuff I need and where to get it and quickly install it, so I have no need for those anymore.

---

### Post by arnieboy on 2007-01-06
> **sjau said:**
> But all they do, you can also do with synaptic or adept (or the shell commands apt-get / aptitude).
That is not true at all. Thats the very reason why Automatix exists (because it goes beyond apt and synaptic)

---

### Post by hyper_ch on 2007-01-06
what can't you install with aptitude or apt-get?

---

### Post by teaker1s on 2007-01-06
Automatix easily installs and configures both extra repositories and packages-synaptic can install far more software, though new users aren't familiar with adding sources to make synaptic work.

Automatix is great for quick new pc config, but synaptic has far more scope in general.

---

### Post by d3v1ant_0n3 on 2007-01-06
EasyUbuntu and Automatix are both great 'setup' tools (for using on a fresh install to quickly install lots of handy stuff. I personally prefer Automatix, never managed to get EasyUbuntu to behave properly. But that was probably my own fault. Automatix also has a lot more in it (or at least compared to when I last checked EasyUbuntu.

Both EasyUbuntu and Automatix can only install a certain variety of programs tho', whereas Add/Remove and Synaptic both have access to everything in Ubuntu's repos (and any 3rd party repos you care to add).

Add/Remove Programs and Synaptic are both frontends to apt-get -which allows you to download programs from the repositories. I prefer to use apt-get from the terminal to install programs when I know the package name, but if not, I'll use Synaptic. It's just more comprehensive.

---

### Post by 2CV67 on 2007-01-07
Thanks guys for those helpful answers.
I guess I have a reasonable idea now of which to use for what purpose. :) 

As nobody mentioned any problems with the two points below...

> **2CV67 said:**
> 
Do they all work in harmony (recognize applications installed by 'rivals') or ignore each other, or screw each other up? (I mean if they are used one at a time, not if I tried to use them exactly at the same time...)

Do I have to remove applications with the same tool I add them?


...then I assume they cooperate well & I don't need to remember which one to use to uninstall with.

Please SHOUT if that is not true!

Thanks again!

---

### Post by MetalMusicAddict on 2007-01-07
I would stick entirely with Synaptic.

---

### Post by antharr on 2007-01-10
Everytime I use Automatix, my system starts freezing and wil not shut down properly.

---

### Post by hyper_ch on 2007-01-10
I would also only use synaptic/adept/aptitude/apt-get - whatever you prefer... and learning how to manage the repositories and how to enhance them...

---

### Post by Zzl1xndd on 2007-01-10
> **sjau said:**
> I would also only use synaptic/adept/aptitude/apt-get - whatever you prefer... and learning how to manage the repositories and how to enhance them...

I agree I only use Automatix now when setting up a system for someone else it just makes it quick and easy :) but if your really looking to learn its not much help.

---

### Post by MkfIbK7a on 2007-01-10
> **arnieboy said:**
> That is not true at all. Thats the very reason why Automatix exists (because it goes beyond apt and synaptic)

this is very true,
if you could do all the things automatix can do with synaptic what would be the point...
in my opinion automatix is a very good because installs things that would take **_ALOT_**  longer and would take alot of command line use in minutes.

I have never had a problem with automatix (though some people do not like it, dont ask me why[-( ) .

for installing all the things that you may need 
(other than the things automatix has)
if you want a gui app use synaptic
for a command line app use 
apt-get or aptitude.

my 2 cents worth[IMG]http://www.pctalk.info/forums/images/smiles/icon_2cents.gif[/IMG]

---

### Post by t0t0 on 2007-03-09
From my experience they all work together with no problems. 

I now avoid Automatix now because every time I have installed it my system hasbecomes unstable; Easyubuntu seems to behave a bit better.

---

### Post by igknighted on 2007-03-09
> **hyper_ch said:**
> what can't you install with aptitude or apt-get?

Swiftfox, Songbird, and many other programs Automatix installs are not in the repos.  These would otherwise need to be installed by hand.

---

### Post by hyper_ch on 2007-03-09
Automatix is not necessary... you can do it "manually" which means you will have to take some additional steps for a few things... but it normally can also "easily" be done.
E.g. for extra codecs you just have to
(1) add Seveas' repository
(2) import Seveas' repository key
(3) update your sources
(4) install the according libraries...

or

(1) download the source from some site
(2) configure and make it
(3) install it

I tend to think you learn a lot more by doing this manually than through automatix...

I know, as first-time user automatix is great, I used it myself, but meanwhile I don't anymore because I don't know how it will affect the overall system.

Once you figured out how to manually do this you can then write some kind of shell script yourself that will do those steps next time automatically...
I have written for myself a small "install.sh" which replaces my repo files to the one I want, download and install the according keys and install the software I need... a reinstall of my system can be done fairly quickly.
Last weekend I changed from Edgy to Feisty and I had it running in quite a short amount of time (I made a new install as I also got myself a 500gb drive)...

---

