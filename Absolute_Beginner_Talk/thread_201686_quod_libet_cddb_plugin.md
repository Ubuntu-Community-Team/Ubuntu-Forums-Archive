---
title: "quod libet cddb plugin?"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by joris1977 on 2006-06-22
Just discovered the quod libet music player. I like it because of the tagging options, so  it's a bummer  i couldn't get the cddb tagging plugin to work yet. I installed the quodlibet package and quodlibet-ext and the quodlibet-plugins with the synaptic package manager. 

when i try to run the cddb plugin. it says under plugin errors: 

brainz:

Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/brainz.py", line 4, in ?
    import musicbrainz, os, gtk
ImportError: No module named musicbrainz

Does anyone know any simple solution for this?
I search forums and google but i couldn't  find a solution for this.

---

### Post by hugmenot on 2006-06-22
python-musicbrainz is the package you need.

BTW I uploaded newer packages to the thread titled roughly HOWTO isntall latest Quod Libet.

---

### Post by joris1977 on 2006-06-22
thanks for replying hugmenot,

 i installed all the packages you posted in you uploaded in the threat (howto quod libet). At first there was a dependecy problem but synaptic repaired (or removed not sure)  the broken package  and then i could reinstall succesfully the exfalso package.

but in quod libet the problem mentioned still remains and  a new error shows up: Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/lastfmsubmit.py", line 11, in ?
    import lastfm
ImportError: No module named lastfm

I don't care about the lastFM plugin, but i don't really feel like  getting closer to using the cddb plugin.... ;)

btw I'm using dapper so i allready figured out i needed python-tunepimp instead of musicbrainz...but nothing changes....

btw2: After i installed quod libet today i thought i finally found a good foobar2000 replacement, i don't like most mediaplayers in linux, who want to manage your library (like banshee or amarok): cause my library is way too big and changes often... That's why i was disappointed to find out that Quod Libet doesn't play wma... (I know wma sucks, but i've got some music in this format)

---

### Post by hugmenot on 2006-06-22
> **joris1977]thanks for replying hugmenot,

 i installed all the packages you posted in you uploaded in the threat (howto quod libet). At first there was a dependecy problem but synaptic repaired (or removed not sure)  the broken package  and then i could reinstall succesfully the exfalso package.

but in quod libet the problem mentioned still remains and  a new error shows up: Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/lastfmsubmit.py", line 11, in ?
    import lastfm
ImportError: No module named lastfm[/QUOTE]

Ah, forget about that one, I deleted it already many times but it is retrieved again every time I do a checkout. The QL scrobbler plugin does the same thing.

[QUOTE]I don't care about the lastFM plugin, but i don't really feel like  getting closer to using the cddb plugin....  said:**
> 

No that&#8217;s a false myth that I put out, a misconception. You do need python-musicbrainz. It was mentioned by luks that he has Dapper versions of this package in his MB repository.

Actually for CDDB (which is really a *FreeDB* client) you don&#8217;t any musicbrainz but the python-cddb package. You weren&#8217;t aware of that because it&#8217;s a &#8220;Recommends:&#8221;.

[quote]btw2: After i installed quod libet today i thought i finally found a good foobar2000 replacement, i don't like most mediaplayers in linux, who want to manage your library (like banshee or amarok): cause my library is way too big and changes often... That's why i was disappointed to find out that Quod Libet doesn't play wma... (I know wma sucks, but i've got some music in this format)

I don&#8217;t have a single wma file...:neutral:

---

### Post by joris1977 on 2006-06-22
thanks again hugmenot  

I downloaded and installed python musicbrainz from luks repositary and the python cddb package from 'normal' repositaries but the errors remain when I check the show errors box...

 what the ****! but who cares cause the plugins are working fine. :) Yes!

Quod Lib really is fine app : lyrics support, album art and easy tagging who wants wma anyway...  (well beep will play them if necessary)  

Goodbye Foobar2000.....

---

### Post by sha_man on 2006-07-03
bad news, but f*reedb ist dead* :cry:

---

