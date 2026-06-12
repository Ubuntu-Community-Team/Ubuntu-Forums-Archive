---
title: "Conver avi to wmv"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by tomt on 2007-05-19
Is there any way I can convert avi files to wmv files?

Also HAS ANYONE found a way to stream to the 360 from linux. I think it blows that you need wmc or some such.

---

### Post by cody50 on 2007-05-19
for converting I know of a handy online file conversion site [www.zamzar.com](www.zamzar.com) . It works nice but as far as local conversion I havent done much of that.

---

### Post by Quicky on 2007-05-19
I use [Twonkymedia]("http://www.twonkyvision.de/") to stream to my 360. Its proprietry, but its awesome - there's a 30 day trial available if you want to check it out. It will stream photos, music and wmvs to the console, but unfortunately for me any videos I grab from my handycam in Kino are exported as mpegs, and without wmc you can't stream any videos with a codec of anything other than wmv.

I've been searching for a way to convert my mpegs to wmvs but I haven't come across anything that will do it in linux. There are some threads on here that claim that you can use ffmpeg to convert to wmv but all my experimenting with that has resulted in failure. The the resulting conversions *look* like wmvs but for whatever reason, the 360 refuses to play them. If anyone has had any success with that I'd like to hear about it.

---

### Post by starcraft.man on 2007-05-19
You know... this is just a crazy thought here but with all the trouble your gonna go to converting AVI to WMV (I wouldn't its a stupid MS format...) and then finding a program to stream em to your xbox/use that paid product. You do know there is a media platform called [mythTV]("http://en.wikipedia.org/wiki/MythTV") right? It isn't that hard to set up, while I haven't done it myself I've seen it in action and its pretty good. All ya need is some old PC (not too old, p3 and up should do it I guess) with the right inputs/outputs for your TV (can get a cheap card) and then install it on the PC hook it to your TV and boom you have a recording multimedia platform right there, you can record the TV to your hard drive and move it around in your home via your network and put any movie you want on it..

Ya may find that to be a much better thing for you, and best of all it has nothing to do with MS and theres no lock in for the format/DRM/anything else.

Choice is yours, just putting it out there.

---

### Post by Quicky on 2007-05-19
Cheers Starcraft, but that's a solution to someone else's problem. I already have a wireless network that is capable of streaming my media to my media extender (the Xbox 360) – it already streams all my photos and music (even during games) and would also do all my videos if it weren't for the fact that the majority of them aren't encoded using the codec required. Its a shame that MS will not support other codecs on their console, but I accept that.

Having nothing to with Microsoft isn't an issue either. Sure I'm not a fan of Windows, but the 360 is probably the best piece of gaming kit I've ever come across. The company behind the products I like is irrevlent to me.

Being able to convert to wmv using a software solution (while I agree that using a more open codec would be preferable) is by far the simplest way achieving the results I want. Thanks for the input though mate.

---

### Post by newlinux on 2007-05-19
I'm pretty sure ushare can stream to an xbox 360, in certain formats. It's used by GeeXboX.

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

i use twonky as well (not with an Xbox 360, but with my networked DVD player). Mythtv Actually comes with a UPnP server as well, but at this point I think it only serves up its recordings, not images or music, through UPnP -- that's all I've used it for, and for myth's recordings, it works rather well.

---

### Post by Quicky on 2007-05-20
Looks like ushare can stream to the 360 but only with a particular firmware verison. The last two updates to the Xbox's dashboard have caused problems with third party UPnP software and that's part of the reason I chose to go with Twonky – within days of an update to the 360 they always release an updated version of their software which ensures full functionality. Ushare doesn't support dashboard revision 2.0.5759 just yet.

There's still the same problem with video streaming though – the 360 will only accept streamed wmv so the conversion issue remains. It looks like a good free alternative to Twonky though for anyone that wants to try it.

---

### Post by tomt on 2007-05-20
Quicky-thanks for the help. I am having some difficulty configuring Twonky but working away at it.

Do you know any good tutorials out there on getting twonky set up and getting the xbox to pick it up?

I've taken a look but everything seems to be in german...

---

### Post by Quicky on 2007-05-20
I can tell you what I did if that will help.

[LIST=1]
[*]Download the Twonky trial to your home folder from here: [http://www.twonkyvision.de/Download/TwonkyMedia/index.html]("http://www.twonkyvision.de/Download/TwonkyMedia/index.html"). Make sure you get the Linux x86 (for manual installation) version. The filename is twonkymedia-i386-glibc-2.2.5.zip
[*]Create a folder called twonky in your home folder, and extract the contents of the zipfile to it.
[*]Start the server in a terminal with: /home/yourhome/twonky/twonkymedia
[*]You can configure your media folder locations with the twonkyvision-config.html file in your twonky folder. Double click it to open in Firefox. I've set up three content locations – one for music, one for pictures and one for video. It should be fairly obvious how to do that on the web page.
[*]Once you've done that, save the changes and hit 'Rescan content directories'. Give it a minute or two to index your media.
[*]Switch on the 360 and go to the media blade. Choose pictures or music and select 'computer' You should see a long server name for Twonky appear – choose that and you should get access to your media. Any WMVs you have will appear in the videos part of the media blade also.
[/LIST]

Be aware that you'll need to have the latest Xbox firmware version from Live on your 360 (the Spring update), or at least the autumn update from last year as video streaming was not implemented for UPnP servers until then.

I also made sure that in my firewall settings within Firestarter the inbound traffic policies allow connections from the Xbox's IP address. You may encounter problems otherwise.

If everything is succesful you'll probably also want the server to run on startup so that you'll always have access from your console, so in Ubuntu go to System-Preferences-Sessions, click the Startup Programs tab and hit Add and paste in /home/yourhome/twonky/twonkymedia.

Let me know how you get on.

---

### Post by gamma on 2007-05-31
Apparently with the latest firmware the 360 can stream MP4 w/ AAC audio saved as a .mov file. Guide here:
[http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/](http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/)

---

