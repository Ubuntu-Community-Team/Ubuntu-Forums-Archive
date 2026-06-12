---
title: "how come i can't view dvd's?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-11
i have a cdrw-dvd rom. i tried to view a dvd and got the message in the attachment. i looked up the libdvdcss and it was already installed. is there another dvd software i can add? i tried using mplayer and it too didnt work. i downloaded ogle and it didnt work either.

any ideas?

---

### Post by r3st on 2006-06-11
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

you might want this too
[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by maddbaron on 2006-06-11
what is the gnome-look supposed to do?

---

### Post by Jason_25 on 2006-06-11
How did you install libdvdcss?  Did you install a deb, or compile it properly using the restricted formats page?  I suggest following the restricted formats page to a tee once you have removed what you have already done.

I think he linked gnome-look because your desktop is so ugly.  But you'll have time for all that once you get the basics working.

---

### Post by maddbaron on 2006-06-11
my desktop is fine to me thanks.its black art. i'm black and its historic art called after the dance i enjoy it and its far from ugly. its black people having fun and black people aren't ugly. i also have 4 panels which i like and 4 pieces of black art which i also like. as a black man i LIKE IT.

the gnome-look.org wall papers are UGLY to me thats y i didnt use them.

ok?

anyway i fixed the problem i didnt compile just downloaded the lib. now complied and working.

---

### Post by mdsmedia on 2006-06-11
personally, I like your wallpaper, and I'm not black. Where can I find that picture?

---

### Post by racecat on 2006-06-11
What's wrong with installing from a deb on this? I downloaded libdvdcss from freshmeat and ran dpkg -i and it worked perfectly.

BTW maddbaron, I like the wallpaper, too. Can't comment on the Gnome part. I like KDE soooo much better. Having choices is a beautiful thing.

Bill

---

### Post by maddbaron on 2006-06-11
i googled black art was looking for a specific artist and this came up in google images i had seen it b4 but couldnt find a big enough one now i did and it worked. i dont remember the actuall site i found it on tho. i wanted something different and i am proud of my history and i happened to be listening to some marvin gaye as i found it lol so it felt like it was chosen for me.

i downloaded libdvdcss from synaptic but i had to run the compile code which i didnt know about. i read it on the restrictive thing and ran it and now it works....now i need to figure out y my vlc player only plays the sounds of the wmv but not the video even tho mplayer does. and y my mplayer plugin for firefox wont work anymore with wmv but will play wmv when i am not online...very weird the video codes to get things working.

---

### Post by manicka on 2006-06-11
Try using vlc - I never have a problem with it

---

### Post by maddbaron on 2006-06-11
[QUOTE=manicka]Try using vlc - I never have a problem with it[/QUOTE]

for some reason vlc doesnt work for me. it just plays the audio but the video part doesnt show.

its very weird. i googled it and everything it said the something about compiling but thats only for the breezy release according to the site. nothing for ubuntu :(

---

### Post by nalmeth on 2006-06-11
Whats the problem with the mplayer-mozilla? Often with wmv videos I will get weird behavior from it, but usually hitting play again, or giving it extra time makes it work. When all else fails I have the Video Downloader Firefox Extension. You should pick that up anyway, I use it all the time.

How does totem work for you?

---

### Post by jackn on 2006-06-12
Glad it's worked out for Maddbarron, but it hasn't for me.

I'm pretty sure I've done everything by the book, that is by [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats), and I can't play DVD's.

It looks like lots of people can, so I'm hopeful, but right now I can't play DVD's.

Facts: 
1. After having followed the above instructions, I keep getting error messages with with Totem-Xine or Realplayer when I try to play DVD's.

2. When I tried with Ogle, it worked, but without sound.

3. My DVD player kept locking. The region explanation proposed in 'Restricted Formats' doesn't seem to account for it, as it goes on locking after I followed the instructions on that too. I've been trying to play zone 2 DVD's on a zone 2 player.

Help? I'd like to be able to play DVD's and to fearlessly slide a DVD into the tray. Right now, I'm even wary of trying anything, lest my DVD (rented) will get stuck.

Thanks, 
Jackn

---

### Post by Jason_25 on 2006-06-12
Sounds like you have a hardware problem with your dvd drive?  Maybe you should get that sorted first.

---

### Post by jackn on 2006-06-13
Thanks kindly, Jason.

Dual booting with XP, and no problem with the DVD player locking there. It's only ever happened in Ubuntu.

And I don't know whether this issue is related to the inability to play DVD's or not.

---

### Post by Jason_25 on 2006-06-13
Maybe you could check the console output from these apps to see what is wrong.  From gxine you can do this from within the program under "engine log".  For totem, you will probably need to start it from the terminal, and watch what it shows.

When you say the dvd gets stuck, when you restart the computer you still cannot eject the disc?  If this is the case then I would say hardware trouble 100%.  If not, then possibly the dvd was still being used by ubuntu so it would'nt unmount and therefore eject.

---

### Post by jackn on 2006-06-17
Maybe you could check the console output from these apps to see what is wrong. From gxine you can do this from within the program under "engine log". For totem, you will probably need to start it from the terminal, and watch what it shows.

Thanks again, Jason. Am late, as haven't had acces to computer.

OK, developments.

The two issues seem to be separate.

Hardware (CD/DVD player first)
I can recover the DVD upon restarting the computer, it is not stuck forever. As you say, this means, not hardware.
Furthermore, same thing has happened recently with a CD, so issue is with player configuration somehow.
Clue: when trying to look at a CD from places/computer/CD-RW-DVD-ROM-Drive in the GUI, I get the following message:
'Unable to mount the selected volume'.
In 'details', I get:
mount: block device /dev/hdd is write-protected, mounting read-only

mount: /dev/hdd already mounted or /media/cdrom0 busy

mount: according to mtab, /dev/hdd is already mounted on /media/cdrom0

So, apparently, the hdd, mounted for some reason in /media, is not mounted where it's expected to. I don't know where that is.

Could this be related to your idea, that 'possibly the dvd was still being used by ubuntu so it would'nt unmount and therefore eject'?!

Should I mount it elsewhere? Where? Don't know what place in the filesystem the 'CD-RW-DVD-ROM-Drive' icon in 'places' refers to (or how I'd go about finding out).

Video next. 
CAN now play DVD's with Ogle. Haven't explored this enough yet. Will soon start it from the terminal, look at the log and post again.

Thanks a lot for the attention and help.

Jackn

---

### Post by jackn on 2006-06-17
DVD player lockup:

Problem largely solved as my son pointed out I had to tell it  either to 'eject' from the GUI, or to 'umount' from the terminal. I'm just used to doing it with the button of the DVD player. 

DVD playback:

Now that I've looked at Ogle a bit more, I've realized that, while it plays the DVD's with sound, the colours are washed out.

As to Totem, I've done what Jason suggested, and the results are interesting, and probably instructive, although I don't know how to solve this on my own. When I run Totem on the terminal, it fails to play back the DVD, the GUI collapses, and it says:
'(totem:6065): Gdk-WARNING **: locale not supported by Xlib

(totem:6065): Gdk-WARNING **: cannot set locale modifiers
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 70 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)'

I'll add that the 'Xlib' and the 'local modifiers' error messages also occur when I try to do 'gedit', so it could be, as the above says, sth about X windows.
Thanks for the help and attention.

---

### Post by Lord Illidan on 2006-06-17
Try VLC. It is in the repos...

---

### Post by jackn on 2006-06-18
Thanks Lord, I might. It will have been my third video player, at least. Are we saying that Linux is so trashy? Lots of people, I've seen in the forums, do use Totem (Totem-Xine), so it should be possible.

I'm in Linux to learn as much as I'm in it to use, so it's important to me to work out the glitches. In it for the ride.

Jackn

---

### Post by jackn on 2006-06-18
Now it's a big hearty Thank You, Lord.

VLC just works on my machine. Downloaded, hit play, and it did. No washed-out colour, no jerkiness, lovely sound.

I'm happy and grateful.

Jackn

---

### Post by jackn on 2006-06-18
One final word:
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Jackn

---

### Post by Lord Illidan on 2006-06-18
[QUOTE=hroit]Now it's a big hearty Thank You, Lord.

VLC just works on my machine. Downloaded, hit play, and it did. No washed-out colour, no jerkiness, lovely sound.

I'm happy and grateful.

Jackn[/QUOTE]

Ask and ye shall recieve 8-) 

VLC is the best media player out there, I believe. You could have arranged the other players, but the default VLC settings are the best. And it works on Windows, too!!

---

