---
title: "Why at all use Apt-get"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-08-08
Well having read people advising to always use aptitude instead of apt-get because it makes uninstall complete( removes dependancies as well) then why at all have the apt-get command to mislead people in the first place :rolleyes: Any takes on this?

Is apt-get in anyway advantageous or am i missing something obvious here? ;)

---

### Post by anaconda on 2006-08-08
I think so many people are used to using apt-get, 
Old habits are hard to kill.

Becides if I am not wrong, aptitude and synaptic both use apt-get.. They are just smarter layers build on top of apt-get.

And yes it is wiser to use aptitude..

---

### Post by xpod on 2006-08-08
My question presicely....Having been using unbunto for this last week one of the first commands i was advised to use(by somebody with unbunto drip)was the apt-get update and upgrade.

Now i am just starting to discover the apparent dis-advantages of this command as apose to the "aptitude" one.

Well.....at least NOW i know(???):confused:

---

### Post by Brunellus on 2006-08-08
apt-get came first.  As I understand the development of Debian, first there was .deb and dpkg.  The former is the package format, which contains all the files, plus information on dependencies.  The latter is a program that installs .debs.  No more, no less.

Then there was apt.  apt manages dependencies, searches cached package lists, and so forth. 

aptitude came later.

I should use aptitude more than apt-get, but I find that aptitude is just slower to type.  Also, I learned on apt-get and it's tough to unlearn old habits.

Another reason is that apt-* is very easy to get your head around, conceptually.  apt-get invovles package management, apt-cache searches.  

It is possible to have aptitude's cleanup capabilities without aptitude using deborphan and debfoster, but I admit they're not great tools.

---

### Post by vanstrien on 2006-08-08
--My post was completely wrong - so I've deleted it in good taste!--

---

### Post by Brunellus on 2006-08-08
> **vanstrien said:**
> There really isn't any reason to use apt-get, except that unless you want a GUI.

Most newbies should use Synaptic just because it is graphical and they might not be comfortable using a command line tool like apt-get, or a rougher gui tool like aptitude.

Just to clarify, apt-get installs dependencies and you can uninstall with it just fine.
vanstrien:  you do mean that there's no reason *not* to use apt-get?

---

### Post by hotbrainz on 2006-08-08
Sorry Vanstrien, but i did have problems having to remove my kubuntu packages after having used apt-get.

I does not remove all dependancies. I am sure about that. 

Does Brunellus have something to say on this coz i am not much more than  a mature rookie :D

---

### Post by Brunellus on 2006-08-08
The two tools for cruft management have usually been deborphan and debfoster.... however, a quick check of the project [homepage]("http://www.fruit.je/debfoster/")for debfoster shows that the package is now officially deprecated in favor of aptitude.  

looks like I'm going to have to go to aptitude now, since that's where the official debian line is.

---

### Post by Jagot on 2006-08-08
apt-get does not remove dependencies.  Read this:

[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

---

### Post by xpod on 2006-08-08
Another conflicting piece of advice.....Well,as a newcomer the general consensous seems to me to be to use aptitude because IT is the one that removes all depedancies

I recently seen a comment by a learned member of this community NEVER to use apt-get.

Although i must admit i was`nt sure if he meant for the specific task the newcomer was enquring about OR for ALL relevant tasks.

Ive been using the apt-get for my updates/upgrades SO is that better to use aptitude too

It all gets a bit confusing on top of everything else.....(not complaining...love it:confused: )

---

### Post by Tortanick on 2006-08-08
Yeah I think we really should try and move the community over to aptitude, leaving large amounts of unneeded stuff behind after uninstalltion is bad.

---

### Post by xpod on 2006-08-08
Im probably leaving ALLSORTS lying about no matter what i do but happily the more i do wrong the more i eventually learn............Hopefully.lol

---

### Post by aysiu on 2006-08-08
A while ago, I wrote a thread just like this one. You can read it if you're interested: [Replace apt-get recommendations with aptitude...?](http://www.ubuntuforums.org/showthread.php?t=164082)

Sometimes *aptitude* is a little too "smart" and wants to do things you don't want to do, especially if you have conflicting repositories or have forced newer or older versions of applications. In that case, I would recommend *apt-get*. Also, there are some people (rare though it is) who do not want unused dependencies to be removed, so I would recommend *apt-get* to those people.

Otherwise, *aptitude* all the way.

---

### Post by Dr. Cox on 2006-08-08
does anyone of these programs give me information on the dependencies of certain packages if i think i need to know them? where can i look those dependencies up, otherwise?

do i have to tell aptitude to remove unused dependencies when i tell him to uninstall something or does it to it all by itself?

---

### Post by aysiu on 2006-08-08
> **Dr. Cox said:**
> does anyone of these programs give me information on the dependencies of certain packages if i think i need to know them? where can i look those dependencies up, otherwise? I think the *dpkg* command can help you with that: ```
man dpkg
```

> 
do i have to tell aptitude to remove unused dependencies when i tell him to uninstall something or does it to it all by itself? *aptitude* will remove any dependencies that are unused by other programs. You must have installed with *aptitude*, though. You can't install with *apt-get*, remove with *aptitude*, and expect that same functionality.

---

### Post by andiii on 2006-09-16
> **aysiu said:**
> 
Sometimes *aptitude* is a little too "smart" and wants to do things you don't want to do, especially if you have conflicting repositories or have forced newer or older versions of applications. 
That just happened to me. I clicked ok to remove one unused package taht aptitude had found and it uninstalled about 30 packages... dvd stuff, csh, tcsh, dillo, ffmpeg..

And I have no idea why..

---

### Post by Najand on 2006-09-16
I think why many people (included me) are used to apt-get than aptitude is that, apt-get was introduced to debian since Debian Ver. 2.0 (hamm if I can recall it correctly) and was much easier way than dpkg of Debian... So many people learnt using that because there was a big difference between dpkg and apt-get. However aptitude was appeared since potato (2.2) and although it is a little smarter than apt-get, the difference was not that much to many people to change their habit and start using aptitude instead. It is right that it is smarter, it has a GUI if it used as a command alone and much nicer, but for general usage, I found there is not much difference between any of them during general usage. 
Another reason many people are using apt-get is that Redhat started using that since RH7.0 for some versions before they completed yum from what it was in Yellow Dog... So many ex-redhat users are also familiar with it... Although redhat never showed any interest to aptitude.
It is right... It is better to use aptitude when recommending it to newbies... And let them use it to change the habit of using apt-get at all.

---

### Post by Ziox on 2006-09-16
I love to use aptitude, solving dependencies and all that...but it just might be too "smart"...whenever I do this command:

> sudo aptitude install

aptitude wants to remove grub from my system...why?

---

### Post by picpak on 2006-09-16
I say use apt-get for the small stuff, and aptitude for the huge stuff (eg: installing kubuntu-desktop).  That way, you won't get silly errors like removing grub.

---

### Post by Najand on 2006-09-16
Aptitude alone without any urgument usually acts on any stored or pending actions.

---

### Post by elettronicha on 2006-09-16
> **Brunellus said:**
> I should use aptitude more than apt-get, but I find that aptitude is just slower to type.
You can set some shorter name to aptitude (like "upd" for "aptitude update" or "upg" for "aptitude upgrade") by the alias in your ~/.bashrc file. ;)

---

### Post by Najand on 2006-09-16
> **elettronicha said:**
> You can set some shorter name to aptitude (like "upd" for "aptitude update" or "upg" for "aptitude upgrade") by the alias in your ~/.bashrc file. ;)
Unfortunately you cannot sudo aliases.

---

### Post by zappafrank on 2006-09-16
sure you can. try: 

alias somename="sudo xterm"

for a test ;)

---

### Post by Najand on 2006-09-16
> **zappafrank said:**
> sure you can. try: 

alias somename="sudo xterm"

for a test ;)

Well, first of all:
[COLOR="Blue"]```
alias somename='sudo xterm'
```[/COLOR]
 not
[COLOR="Red"]```
alias somename="sudo xterm"
```[/COLOR]
Secondly, yes... With aliasing sudo, it is possible...

Anyway you don't use "apt-get" because it has one letter less than "aptitude"... There is not so much differnce between typing one letter less or more...

---

### Post by elettronicha on 2006-09-16
> **Najand said:**
> Anyway you don't use "apt-get" because it has one letter less than "aptitude"... There is not so much differnce between typing one letter less or more...
Mine was just an advice to Brunellus, since he said typing aptitude is too long. ;)

I use aptitude because is better to me than apt-get.

---

### Post by Najand on 2006-09-16
I know... Hmm, people can select themselves, if they want to use apt-get or  aptitude...  

Actually removing is not the only difference between apt-get and aptitude.
They use a different methods for registering packages that are on hold. To identify packages on hold for aptitude with
```
# aptitude search "~ahold" | grep "^.h"
```
While if you want to check which packages you had on hold for apt-get, you should use
```
# dpkg --get-selections | grep hold
```

---

### Post by zappafrank on 2006-09-16
[QUOTE=Najand;1506326]Well, first of all:
[COLOR="Blue"]```
alias somename='sudo xterm'
```[/COLOR]
 not
[COLOR="Red"]```
alias somename="sudo xterm"
```[/COLOR]


it doesn't really matter, works one way or the other :)

---

### Post by Rui Pais on 2006-09-16
> **elettronicha said:**
> Mine was just an advice to Brunellus, since he said typing aptitude is too long. ;)

I use aptitude because is better to me than apt-get.

in fact it could be the other way around... 
with bash completion:
apti[TAB] -> aptitude

while
apt-[TAB] -> lists all apt-* i have (9) and to use TAB i have to type apt-g[TAB] one more letter ;)

---

### Post by xpod on 2006-09-16
And there was me thinking i KNEW the differences:shock: .

---

### Post by aysiu on 2006-09-16
Even though *aptitude* is one character longer than *apt-get*, it's still faster for me to type, as it is a real word in the English language, and it doesn't involve a punctuation character (hyphen), which both interrupts the word and requires me to reach up to the top-right of my keyboard (an awkward action).

Is it faster for you to type *pqwrtz* or *firefox*? Technically, *firefox* is longer, but it's made up of two real words and flows more naturally in the mind. The other "word" just looks like a string of random letters.

---

### Post by mlind on 2006-09-16
*apt-get -f install* still works better than *aptitude -f install*, dunno why. Some people may not know that aptitude's default preference is to install Recommended (and Suggested ?) packages too, but this can be avoided with -R option.

aptitude is still lacking some nice features of apt-get, but hopefully these will be added someday.

---

### Post by xpod on 2006-09-16
I was going to comment on the maddness of the"types quicker" thing when i posted before but you do a much better job of it mate

---

### Post by Rui Pais on 2006-09-16
> **mlind said:**
> aptitude is still lacking some nice features of apt-get, but hopefully these will be added someday.

I never noted that. Do you have an example?

aptitude have other features that apt-get don't, like a search option that can be made by any user (without sudo command)
```
aptitude search something
```

---

### Post by elettronicha on 2006-09-16
> **Rui Pais said:**
> I never noted that. Do you have an example?

aptitude have other features that apt-get don't, like a search option that can be made by any user (without sudo command)
```
aptitude search something
```

apt-cache search something

---

### Post by Rui Pais on 2006-09-16
yes, thats right, but thats not apt-get. you need 2 different commands... 
i always wonder why apt-get don't implement a search, maybe calling internally apt-cache... would be extremely simple.

---

### Post by btdown on 2006-09-16
I dont know about anyone else...but I can't figure out how the hell to use aptitude, so i will continue to get apt-get. Its easy to use and hard to screw up.

---

### Post by Rui Pais on 2006-09-16
> **btdown said:**
> I dont know about anyone else...but I can't figure out how the hell to use aptitude, so i will continue to get apt-get. Its easy to use and hard to screw up.

aptitude is only hard to use if launched as a single command (that runs a dos like interface). 
If you use exactly like apt-get is more or less the same syntax. 

You can try: 
sudo aptitude 
and then press TAB key. it will show the available options, they are self-explanatory.

---

### Post by xpod on 2006-09-16
> You can try:
sudo aptitude
and then press TAB key. it will show the available options, they are self-explanatory.

Hey Hey......learn something new each day.Cheers for that.I take it that "tab" thing can be done with other commands to list the options too?

---

### Post by Rui Pais on 2006-09-16
> **xpod said:**
> Hey Hey......learn something new each day.Cheers for that.I take it that "tab" thing can be done with other commands to list the options too?

yes, of course.
bash completion is always improving. In dapper not only shows the available executables on path environment and files on your path, as it will show the option for a lot of applications making the terminal much more comfortable :)

[Never underestimate the power of TAB key!]("http://download2.centerclick.org:81/data/EmlZC2KtMk_SuXwpseKS4Q/videos/simpsons/to_start_press_any_key.mov")

---

### Post by Bill_MI on 2006-09-16
Deleted... made a new thread: [http://www.ubuntuforums.org/showthread.php?t=258890](http://www.ubuntuforums.org/showthread.php?t=258890)

---

### Post by Dinerty on 2006-09-16
For small install's I usually use apt-get, but with big installs e.g kde I used aptitude.

But in reality aptitude would be the better choice for all, just to lazy to break out of apt-get I suppose :(

---

### Post by mlind on 2006-09-16
> **Rui Pais said:**
> I never noted that. Do you have an example?

aptitude have other features that apt-get don't, like a search option that can be made by any user (without sudo command)
```
aptitude search something
```

Can't you use apt-cache search without sudo ?

The features I miss are:
[LIST]
[*]apt-get source
[*]apt-cache showsrc
[*]apt-cache **madison** (this one is nice).
[/LIST]
aptitude changelog is something essential that apt is lacking.

---

