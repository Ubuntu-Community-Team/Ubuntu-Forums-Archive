---
title: "Taking MP3s from a CD..."
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Magneticgravity on 2007-08-25
OK, im dragging some music files from a CD onto a folder called 'music'.

Ok some artists cant get copied though...whats going on?

Something to do with root again!!!?

---

### Post by Magneticgravity on 2007-08-25
Hmmm...

---

### Post by p_quarles on 2007-08-25
I take it this CD consists only of data (MP3) files, and no actual audio tracks? If you want to convert audio tracks to data, you'll need to rip them using an app like Soundjuicer.

And make sure the destination folder is in your /home/username directory. If it's anywhere else then, yes, you will run into permissions issues.

---

### Post by fenian on 2007-08-25
Is this a commercial cd or one you created yourself?

---

### Post by Frak on 2007-08-25
Your problem is most likely what p_quarles stated above.

---

### Post by Magneticgravity on 2007-08-25
OK, its a created CD with mp3s on.

Sound Juice is not recognising any CD, although its on my desktop and i can click on it, seeing all the songs.

---

### Post by fenian on 2007-08-25
If its copying some of the files but not others its probably not a permission problem.Perhaps the disk is not clean or scratched.

---

### Post by Magneticgravity on 2007-08-25
OK, on further speculation, it seems all the song files are m4a.

I downloaded Banshee, but it seems it too cant play it.

I imagine its the song files yes, what can Ubuntu play then??

---

### Post by fenian on 2007-08-25
Open synaptic manager and search for aac install the following...

libfaac0
libfaad2-0
libmp4v2-0

---

### Post by p_quarles on 2007-08-25
M4As, huh? You didn't, by any chance, create this CD with iTunes files, did you? 

Anything that was actually purchased from the iTunes music store is going to have DRM that allows it to play only in in iTunes (or on your iPod). To move that to Linux, you will need to burn the music as audio, using iTunes. Then you'll be able to re-rip it. 

Anything you ripped from a CD using iTunes, though, should be playable with the Linux version of Quicktime.

---

### Post by Frak on 2007-08-25
There's a Linux version of Quicktime?

---

### Post by Magneticgravity on 2007-08-25
> **p_quarles said:**
> M4As, huh? You didn't, by any chance, create this CD with iTunes files, did you? 

Anything that was actually purchased from the iTunes music store is going to have DRM that allows it to play only in in iTunes (or on your iPod). To move that to Linux, you will need to burn the music as audio, using iTunes. Then you'll be able to re-rip it. 

Anything you ripped from a CD using iTunes, though, should be playable with the Linux version of Quicktime.

OK, yes i did, hehe. So, i shud be able to put these files on to Ubuntu with Quicktime you say?

---

### Post by fenian on 2007-08-25
I can play m4a files by using the packages i described above.

---

### Post by p_quarles on 2007-08-25
> **Frak said:**
> There's a Linux version of Quicktime?
It's not actually by Apple, but yes:
[http://linux.softpedia.com/get/Programming/Libraries/Quicktime-for-Linux-257.shtml](http://linux.softpedia.com/get/Programming/Libraries/Quicktime-for-Linux-257.shtml)

> I can play m4a files by using the packages i described above.
That's a much better solution than Quicktime. M4A is just Apple's fancy name for MP4s, so that will work. On everything *except* DRM'd files.

---

### Post by fenian on 2007-08-25
I think if you also intall xine-extracodecs it willl work with DRM'd files but I'm not positive I've never bought music from Apple.

---

### Post by Magneticgravity on 2007-08-25
OK, i inserted a commercial CD - Soundjuicer extracted these files and i chose Og.

All the tracks play in Soundjuicer and Banshee like i expected.

Now...if i went back to itunes and copied a disc again, could i somehow make it so it would work when i next inserted it on Ubuntu,

Could i do that now with the created CD i now have.

---

### Post by fenian on 2007-08-25
You need to burn the disc as an audio cd in itunes and then use soundjuicer to rip it in ubuntu.

---

### Post by Magneticgravity on 2007-08-25
> **fenian said:**
> You need to burn the disc as an audio cd in itunes and then use soundjuicer to rip it in ubuntu.

OK sorry, i guessed i should said i used a DVD but thanks anyway, still new to Ubuntu :)

So, i just burn as an audio cd on iTunes, simply making a playlist like usual, then juicer will extract?

And should i always extract as Ogg, ive heard its a good file type for music.

---

### Post by fenian on 2007-08-25
If you have an ipod or other mp3 player ogg may not be best (some players will play ogg file some like the ipod won't) otherwise ogg works fine.I usually rip my cd's to mp3 with a high bitrate.

---

### Post by Magneticgravity on 2007-08-25
> **fenian said:**
> If you have an ipod or other mp3 player ogg may not be best (some players will play ogg file some like the ipod won't) otherwise ogg works fine.I usually rip my cd's to mp3 with a high bitrate.

I have an iPod. I downloaded Banshee because i heard it supports iPods and i could put music on my iPod etc.

What music player do you use? What would you recommend? Also, ive got gtkpod, which i believe lets you sync your ipod and stuff.

---

### Post by p_quarles on 2007-08-25
You can get .ogg files to work on an iPod by replacing the firmware with the free Rockbox. I haven't tried it, since my MP3 player is unsupported, but I understand it works very well with the iPod. 

I use Amarok for music. Personally, I think it's the most feature-rich media player in the Ubuntu repositories (and, thus, also the slowest, but hey . . .). Again, I don't have an iPod, but Amarok does a good job managing my player.

---

### Post by Magneticgravity on 2007-08-25
> **p_quarles said:**
> You can get .ogg files to work on an iPod by replacing the firmware with the free Rockbox. I haven't tried it, since my MP3 player is unsupported, but I understand it works very well with the iPod. 

I use Amarok for music. Personally, I think it's the most feature-rich media player in the Ubuntu repositories (and, thus, also the slowest, but hey . . .). Again, I don't have an iPod, but Amarok does a good job managing my player.

OK, so if i extracted a CD onto Ubuntu using the Juicer and made them Ogg files.
I can then play it using Banshee, Now if i successfully connected my iPod, could i simply put those Ogg music files onto my iPod (knowing Apple that wont happen).

So, do i need something, or is there an option when extracting a CD to make the music files mp3?

---

### Post by fenian on 2007-08-25
I have an ipod which is why I rip my music to high bitrate mp3 (ogg won't work on the iPod).Rhythmbox and Amarok seem to work the best with it Banshee was kind of buggy.I use[ Amarok]("http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/").I would only recommend using Rockbox if you have a lot of ogg or flac files that arent supported by the iPod firmware,it just doesn't work as well as the default firmware  
(eats up the battery life,choppy playback & other issues).

---

### Post by p_quarles on 2007-08-25
> **Magneticgravity said:**
> OK, so if i extracted a CD onto Ubuntu using the Juicer and made them Ogg files.
I can then play it using Banshee, Now if i successfully connected my iPod, could i simply put those Ogg music files onto my iPod (knowing Apple that wont happen).

So, do i need something, or is there an option when extracting a CD to make the music files mp3?
Apple's firmware will not play .ogg files, no. But like I said, you can install Rockbox on your iPod (this is replacement firmware, available for free), and that does have .ogg support.

And, yes, you can also extract MP3 files from an audio CD. Sound Juicer will do this for you. You have to have the MP3 codec installed first, of course.

EDIT: Re Rockbox: listen to actual iPod owner (i.e., the previous post) -- if it eats the batteries, it's easier just to use high-bitrate MP3s.

---

### Post by Magneticgravity on 2007-08-25
> **p_quarles said:**
> Apple's firmware will not play .ogg files, no. But like I said, you can install Rockbox on your iPod (this is replacement firmware, available for free), and that does have .ogg support.

And, yes, you can also extract MP3 files from an audio CD. Sound Juicer will do this for you. You have to have the MP3 codec installed first, of course.

EDIT: Re Rockbox: listen to actual iPod owner (i.e., the previous post) -- if it eats the batteries, it's easier just to use high-bitrate MP3s.

OK, ill use mp3s from now on, so how do I know if ive installed MP3 codec, i think i have...

---

### Post by fenian on 2007-08-25
From the Applications menu select Add/Remove.In the window that opens search for MP3
choose gstreamer extra plugins,gstreamer ffmpeg video plugin and Ubuntu restricted extras.Click the apply button and it shoul install almost everything you need except lame to install lame do this...

> sudo apt-get install lame

---

