---
title: "[SOLVED] Totem youtube plugin doesn't play video."
date: 2008-11-07
forum: Apple Hardware Users
---

### Post by milkwood on 2008-11-07
Hi,folks!

I've got a problem which is a little complicated.
I could play youtube video with totem youtube plugin on hardy before.
I mean Totem played youtube video directly before I had reinstalled hardy once again.
Video search is Okay.
For example,I search "vertigo" in search window and hit the enter key and the results shows up.
Then double click it's thumbnail and an error occurs saying 
"ffdemux_swf: Element doesn't implement handling of this stream. Please file a bug".
Then I googled about it.
I found and looked at several bug reports to resolve this problem.
One of them described relatively in detail.
I'm sorry I can't remember where did I find that page.
I followed all of that but nothing changed.
Totem says "ffdemux_swf............."as same as old.
I'm wondering this is totem's problem or the problem about flash things?
Gstreamer plug-ins are perhaps fine.I'd had installed most of all.
Maybe I just have to wait until this bug will be fixed though,anyone knows about this?

Thanks in advance.

---

### Post by milkwood on 2008-11-07
Although I don't know how should I say,Why totem can play youtube's files with it's function?
Totem plays sources of youtube's files from it's storage?
Does Totem play embedded files from youtube directly? 
Mine can play ".flv" files that I downloaded.
That's wired.
If I can not play flash files(which I had downloaded from youtube)with Totem,I think it should be so. 
But it's fine.
Another thinking,is Totem doing anything,for example,kind of converting files to it's preference and so on, during playing videos?
But it's no way.My low spec should take reasonable time to do that.
As I mentioned,I could do this before and the movie which I choosed was played very instantly.
Any idea?

Thanks.

---

### Post by cyberdork33 on 2008-11-07
Are you on PowerPC? Please be sure to identify your hardware when posting questions.

---

### Post by milkwood on 2008-11-08
Sorry,I've been a PowerPc user for a long time.
Recently I've also been so called "Obamania".
Anyway,I'm serious.
When I could play before,I had tried several things.
For example,compiling "miro" from it's source or compiling "gnash" as well.
Both failed because of some possible reasons though,hahaha.
I will describe that details in other thread sometime later.
And I installed some applications from repository and it's following dependencies.
On top of that I had set up pulseaudio things soon later .
Then I'm not sure it was before or late that,
"miro" installed from repository had suddenly succeeded it's booting couldn't before.
I just wondered about that and just felt kinda lucky me!
Now that miro is rather no use for me though.
But I think these maybe nothing to do with this current problem.
I should have been installed all dependencies that I installed before.
However,I have another thought that compiling processes might give something special to my patient which deserved it.
I maybe immature more than being atheist.
Perhaps that's why I've got that problem.

By the way,anyone has any idea?

Thanks.

---

### Post by milkwood on 2008-11-09
I've forgotten to write what I did.
I opened terminal and typed sudo gedit /usr/lib/plugins/youtube/youtube.py(as root).
And found this line "relevant line if registry.find_plugin ("flvdemux") == None or registry.find_plugin ("souphttpsrc") == None:" in it.
Then I erased it's latter line "or registry.find_plugin ("souphttpsrc") == None".
Then I saved the file.
But it did't work for me.
And I tried to check some conflicts by install or not install each gstreamer plugin(for example,not install maltiverse basic only etc).
But neither does it.
Others say you should upgrade to intrepid and everything is gonna be fine and you'll get extras.
I agree.
Maybe I should do that or not.
Well,I will think about that in a long term.

Anyway,thanks.

milkwood.

p.s. I've fianlly gotten vlc player working for me.
But at the first time when I played a file,I got a very noisy sound.
Here is my tip.
Open Settings>Preferences>Audio>Output modules and select "ALSA audio output".
Then  select "ALSA" below "Output modules",and hit "Refresh list",select below "hw:0,0".
It works for me.
It doesn't work on Firefox though.
By the way,you know Opera community introduces "ubuntu and opera" at it's Homepage.
If you have something to want to say with that,why not leave your comment there?
:guitar:

---

### Post by milkwood on 2008-11-11
I did a lot.
Do you know "launchpad in ubuntu"?
You just can google "launchpad ubuntu".
I'm convinced this problem is caused by gstreamer-bad-plugin by 88.6 % of my confidence.
I installed old bad-plugin's deb file from launchpad(of course ppc version).
And installed it(make sure don't install the latest version,check out it with synaptic and etc).
But it didn't work as usual.
Then I compiled bad-plugin from source.
But it didn't work,too.
I think this is a bit complicated problem as I mentioned before.
It might happen to something to do with kernel version as usual.
In that case,I have to give up this thing so far.
I can understand NEW features draw new interests,but Hardy is a long term stable version,isn't it?
It'll be fixed one day?
I don't care whether totem can play youtube or not.
Even if you can play youtube,it's not useful if you don't know where particular video you want to watch is(but video search is useful though).

By the way,Would you like to hear what I want to watch in youtube?
I will tell you when you ask me.

---

### Post by ubuntubrian on 2008-11-11
I upgraded both of my notebooks, PPC to Intrepid and the YouTube plays on totem with no problems. the upgrade was rather messy though and I have a problem with firefox crashing when I open a Youtube video.

---

### Post by milkwood on 2008-11-12
Thank you for your information,ubuntubrian!
I would very appreciate your "Intrepid".
Haven't you been PPC users for a long time by now?
Me,too.
I've finally gotten some desktop tips so that I'd like to show you guys my desktop right now.
I've never been able to play Youtube on Firefox though.
I guess gnash has been very improved on intrepid.
Thus I can imagine easily that I would have been enjoying some online flash games by now if I had succeeded in installing intrepid.
Any way,I don't care such a tiny thing.
Make sure if you guys are using a long used machine,each problems might be caused it's own problem.
In fact,I've got a new used machine by less than $100 recently.
I had been holding a power management's problem when I used old one.
But It's problem rooted in it's own problem.
Then that machine had broken because of it's own hardware problem.
My new gotten machine doesn't has this problem.
It can shut down very exactly!
I just think Linux is too disagreeable particularly for minorities as Mr.Darcy was. 
Sometimes I think if you were sick,you should be caught by very common sick.
Because there are plenty of precedents.
But I always stand for minorities,of course,sometimes not though.
That's why I've got these problems.

Thanks.

milkwood.

---

### Post by racoq on 2008-11-15
> **milkwood said:**
> Hi,folks!

I've got a problem which is a little complicated.
I could play youtube video with totem youtube plugin on hardy before.
I mean Totem played youtube video directly before I had reinstalled hardy once again.
Video search is Okay.
For example,I search "vertigo" in search window and hit the enter key and the results shows up.
Then double click it's thumbnail and an error occurs saying 
"ffdemux_swf: Element doesn't implement handling of this stream. Please file a bug".
Then I googled about it.
I found and looked at several bug reports to resolve this problem.
One of them described relatively in detail.
I'm sorry I can't remember where did I find that page.
I followed all of that but nothing changed.
Totem says "ffdemux_swf............."as same as old.
I'm wondering this is totem's problem or the problem about flash things?
Gstreamer plug-ins are perhaps fine.I'd had installed most of all.
Maybe I just have to wait until this bug will be fixed though,anyone knows about this?

Thanks in advance.


This error was caused because of a change on youtube services, leading to the old youtube.py, that is used on the totem, obsolete .

I have uploaded a fixed youtube.py, to launchpad, for all the Hardy users (and only for Hardy), since Intrepid Users are no longer affected with this error, with the latest updates.


see the following link, for the file and instrucions and test it ;) works ok for me :)

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/288494](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/288494)

See the following link

---

### Post by milkwood on 2008-11-16
Thank you for your information,racoq!
I've finally gotten "vertigo" playing on my totem!
I can enjoy watching my favorite videos without downloading them from youtube now.
And I try to force bbc plugin into totem plugin.
But,of course,it didn't work as usual.  
And just one thing left,I also have H264 plugin.
But It didn't work either saying "ffdemux...bra bra bra" as it was.
Well,I shouldn't care this anymore.
I'll put an end on this. 
I'm very glad to see this historical day.
Thanks everyone,God bless you!
This is my first "solved" post!

---

### Post by milkwood on 2008-11-16
No!This is not solved yet!
I've noticed my totem is playing "h264" file with new youtube.py not "flv".
I wondered "why totem plays some files that awkwardly?".
And I thought my low spec machine can't deal with its process.
Then,in fact,I've been known that totem or others can play .flv file directly from clipNabber or keep vid
or wherever you would like to use for downloading movies by using each download links,
I tried these links and totem played them fine.
But when I tried mp4 links it was not fine.
(It's also might be something with my connection speed though.)
Therefore I've concluded my totem is playing "h264" file not "flv".
Do you know where should I modify in youtube.py?
Oh my Goodness...!
To be honest,I don't care of this anymore.
I just think there happen to be some people suffering from this annoying.
If You got a large storage,you don't have to worry about nothing.
To download files is the best:).You can operate them in many ways.
I think this problem is one of the easiest problem in all over the world in the first place for matures.
But for immatures,this is an itch on their back.
That's why this is a little bit complicated problem.
But I feel like I've got something from this.
Thanks!

See ya!

---

### Post by racoq on 2008-11-16
> **milkwood said:**
> Thank you for your information,racoq!
I've finally gotten "vertigo" playing on my totem!
I can enjoy watching my favorite videos without downloading them from youtube now.
And I try to force bbc plugin into totem plugin.
But,of course,it didn't work as usual.  
And just one thing left,I also have H264 plugin.
But It didn't work either saying "ffdemux...bra bra bra" as it was.
Well,I shouldn't care this anymore.
I'll put an end on this. 
I'm very glad to see this historical day.
Thanks everyone,God bless you!
This is my first "solved" post!

Milkwood, sorry i messed up one thing in the youtube.py script (i'm a noob on python), that makes totem drag itself all over the user interface. I basically used a wrong link to retrieve the list of videos on teh thumbnaiil.

Please go get the updated youtube.py on the previous link on the launchpad.


> **milkwood said:**
> ,
I tried these links and totem played them fine.
But when I tried mp4 links it was not fine.
(It's also might be something with my connection speed though.)


That seens to be a gstremer issue, do yout have gstreamer0.10-ffmpeg, or the other gstreamer0.10-xxx family codecs installed?



Best Regards

---

### Post by milkwood on 2008-11-17
Thank you,racoq!
I've confirmed what you said and I think I've got a right file.
I just think that totem's unreasonable play is related with it's own ability.
To say that,youtube provided not good quality movie before,but recently it's changed.
Old files or less qualities are fine.
But good quality files aren't played appropriately with streaming.
Downloaded file is OK:confused:(this maybe not OK now).
If my machine's cpu were high,I wouldn't notice anything
and I would say "why not?What's the matter?".
That's all.
Only I have to do is to prepare alternative ways to watch some videos with downloading them always.
It's a little bothering though.
I don't care anything no longer.
I've gone through a lot of things yet:). 
This is over.
Anyway,Thanks for all your attentions!
By for now!

Try "cp /youtube.py /usr/lib/totem/plugins/youtube/youtube.py".

---

### Post by Philippo.co on 2008-12-05
milkwood!

Thank you so much!

---

### Post by milkwood on 2008-12-05
Hey,Philippo!

It's not me.
You should thank "racog" or others.
I think he(racog) is a nice guy.I can see his mustache.

This is your first post,isn't this?
Therefore I think you are funning of me or thanking me.
Anyway,thank you.

What a boring Friday!

It's just December today,you know?

I'm just bored.

---

### Post by milkwood on 2008-12-08
Hey!

I've been right.
Totem plays .mp4 files.
Confirm that by right clicking thumbnail and choosing copy location and pasting it browser's url window and hitting Enter key.
Then You can download .mp4 file.
If you delete "fmt=18" the last part of the url,you can get .flv file.

Enjoy high quality movies!

By the way,I don't need such a good quality.
Do you happen to know the way to watch youtube of original quality on Totem?
I think I should just modify youtube.py but I have no idea.
All is messed up only I delete one phrase.
It's very sensitive.

Never mind.
This is my latest report.

---

### Post by HeWhoE on 2008-12-25
In the youtube.py script, the subroutine that checks for connection speed, [FONT="Courier New"]get_fmt_string (self)[/FONT], looks into gnome's gconf entry, [FONT="Courier New"]/apps/totem/connection_speed[/FONT].  If the value is greater than or equal to 10, then the "High Quality" file will be streamed.

I've noticed that, on my Intrepid system, there is no such gconf-entry entry.  To remedy this, follow these instructions.

[LIST=1]
[*]Open gconf-editor and go to /apps/totem.
 
[*]Create a new key.
 
[*]Make the key an integer type.
 
[*]Name the key "connection_speed".
 
[*]Set the value of the key to 10.
[/LIST]

On my Mint Elyssa system, I found that the entry exists but was set to 2.  Changing the value to 10 makes the Totem stream the "High Quality" YouTube files.  I don't know if this is also an issue in the standard Hardy distribution, but it's probably not.  I don't remember having the problem with Hardy.

[SIZE="3"]milkwood[/SIZE], if you want to watch the regular quality files, just change the gconf key to a value less than 10.  

By the way, an updated version of the init7 H264 plugin, which resolves the ffdemux brassier error, has been posted here... 

[http://ubuntuforums.org/showpost.php?p=6425919&postcount=4](http://ubuntuforums.org/showpost.php?p=6425919&postcount=4)

---

### Post by milkwood on 2008-12-27
Thanks HeWhoE!
I've just edited networking connection speed from LAN to 56kbps in totem preference and everything is OK now.
I'll give it a try your h264.py!
Thank you.

---

