---
title: "Unable to play music - part two - can't recognize a MP3"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by babel on 2006-04-30
I am just learning the basics of a Ubuntu system.

I decided to try to play some music on the system.

I have already not had success with transferring MP3's to the Ubuntu system via data DVD, so 

I e-mailled them to myself and retrieved them with Evolution.

I moved the MP3's to a new folder called "Music" that I created in my Home folder.

I then opened Rhythmbox music player.  I clicked Music > Import File and browsed to the 

MP3's.  I received this error message:

"Error loading files into library.

The following files couldn't be loaded:

The file is not an audiostream file:///home......."

I tnen doubleclicked directly on the MP3 in my Home folder.  Totem Movie Player opened, 

along with the following error message:  "Totem could not play file:///home........
There were no decoders found to handle the stream.
You might need to install the corresponding plugins"

What should I do next?

---

### Post by Tedd on 2006-04-30
sudo apt-get install lame

Or check the Ubuntu Wiki for "restricted formats."

---

### Post by Buffalo Soldier on 2006-04-30
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by aktiwers on 2006-04-30
[http://ubuntuforums.org/showthread.php?t=157589](http://ubuntuforums.org/showthread.php?t=157589)

Run this script and all formats will work fine! It did for me :)

---

### Post by babel on 2006-04-30
I just read several Wiki articles on "Restricted Formats".
Thanks for pointing them out to me.
I was unaware of this problem.

But since every answer produces at **least** one more question**:**  How do you folks listen to music or watch movies on your Ubuntu machines ?  or are you not able to at all ? Is there a way to convert MP3's to a Ubuntu readable format ?  If so, does it have to be done on a Windows machine since the Unbuntu machine can't read the MP3's in the first place ?  

My "learning curve" on Ubuntu is certainly going to be an adventure !

---

### Post by muep on 2006-04-30
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

has actually instructions for most of the possible formats.

---

### Post by Nequeo on 2006-04-30
[QUOTE=babel]I just read several Wiki articles on "Restricted Formats".
Thanks for pointing them out to me.
I was unaware of this problem.

But since every answer produces at **least** one more question**:**  How do you folks listen to music or watch movies on your Ubuntu machines ?  or are you not able to at all ? Is there a way to convert MP3's to a Ubuntu readable format ?  If so, does it have to be done on a Windows machine since the Unbuntu machine can't read the MP3's in the first place ?  

My "learning curve" on Ubuntu is certainly going to be an adventure ![/QUOTE]

Hey there, 

when you say Ubuntu cannot read MP3s, I'm unsure whether you're referrring to the legal position, or if you kind of misunderstood the article.

Technically, Ubuntu has no problems reading or playing MP3s. It's just not something we can enable by default as it is currently illegal in several countries. Following the links everyone else has posted, you can get MP3 playback working perfectly.

But speaking for myself, I re-ripped my few CDs using Ubuntu's 'Sound Juicer' program. That can save your files as .flac or .ogg, which you could think of as   the Free equivalents of .wav and .mp3. (I'm no expert on media, though, so correct me if I'm wrong).

There are also plenty of programs you can use to convert between media formats. The command-line tool 'sox' is very useful. There is also 'audacity' if you prefer graphical programs.

If you want to do a mass conversion of MP3s to .ogg format, there is a script called 'mp32ogg' also available in the repositories. I've been told that converting from MP3 to OGG reduces the quality of the sound file. I don't doubt that is true, but unless you've got very expensive speakers/headphones, you probably won't notice the difference. 

Hope that helps a little.

Cheers,

---

### Post by aktiwers on 2006-04-30
You dont have to change the format. Run the script I linked to, and you will be up running on mp3, wma and all used formats. I have never had any problems with any formats after running that script!

---

### Post by babel on 2006-05-01
Thanks, muep.  I'll read the MultimediaApplications article over the weekend (the only time I can do more than just scan something quickly).

If I don't find a solution there I'll be back for more specific instructions on how to implement the scripts described by aktiwers and Nequeo (at my present state of knowledge I doubt I can implement them without help!).

---

### Post by babel on 2006-05-03
OK - I read the "Restricted Formats" Wiki article.

I also read an article on "Enabling Extra Repositories"

I opened System > Administration > Synaptic Package Manager > Settings > Repositories.  For each section labelled Ubuntu 5.10 _____ (Binary) I highlighted, clicked "Add" > checked all four components [Officially Supported, Restricted Copyright, Community Maintained (Universe) & Non-free (Multiverse)].

Now, where do I find applications that will enable me to play MP3's & DVD's?

I see in the left-hand column there are sections, for example, Multimedia, Multimedia (Universe) & Multimedia (Multiverse).  Each of these sections, if selected, contain large numbers of applications.

Any suggestions as to which ones I should install to enable me to play MP3's & DVD's on my Ubuntu machine?

How do I install one once I have selected it?

---

### Post by pellgarlic on 2006-05-05
@babel -

in synaptic, there is a "search" field. try searching for "dvd" or "mp3". the results will show the package name, with a description beside it - read the description to decide if it is what you are looking for. 

also, if you search on this forum, and on [www.ubuntuguide.org](www.ubuntuguide.org), you will find specific advice about enabling certain multimedia capabilities. for example, the exact package you need for dvd playback is called "libdvdcss2". (see: [http://www.ubuntuguide.org/#dvdplayback](http://www.ubuntuguide.org/#dvdplayback)) type "libdvdcss2" in the synaptic search, and it should come up.

in the left-hand column, there will be icons - a green square means the package is already installed. a white square means it is "available" for installation. click on the white square, and select "mark for installation" from the popup menu. 

do this for whichever packages you want, then when you are done, click the "apply" button at the top. this will download and install the packages you have selected. you need do nothing more.

voila!

---

### Post by mostwanted on 2006-05-05
[QUOTE=Nequeo]Technically, Ubuntu has no problems reading or playing MP3s. It's just not something we can enable by default as it is currently illegal in several countries. [/QUOTE]

Several in this case meaning the US.

---

### Post by Buffalo Soldier on 2006-05-05
[QUOTE=babel]OK - I read the "Restricted Formats" Wiki article.

I also read an article on "Enabling Extra Repositories"

I opened System > Administration > Synaptic Package Manager > Settings > Repositories.  For each section labelled Ubuntu 5.10 _____ (Binary) I highlighted, clicked "Add" > checked all four components [Officially Supported, Restricted Copyright, Community Maintained (Universe) & Non-free (Multiverse)].

Now, where do I find applications that will enable me to play MP3's & DVD's?

I see in the left-hand column there are sections, for example, Multimedia, Multimedia (Universe) & Multimedia (Multiverse).  Each of these sections, if selected, contain large numbers of applications.

Any suggestions as to which ones I should install to enable me to play MP3's & DVD's on my Ubuntu machine?

How do I install one once I have selected it?[/QUOTE]

Dear babel,

If you have read the restricted format wiki till the end you will find that it contains the complete instruction from A to Z on how to enable everything from MP3, Flash, DVD, RealPlayer, AAC and etc.

---

### Post by n3tfury on 2006-05-05
[QUOTE=Nequeo]

I've been told that converting from MP3 to OGG reduces the quality of the sound file. I don't doubt that is true, but unless you've got very expensive speakers/headphones, you probably won't notice the difference. 

Hope that helps a little.

Cheers,[/QUOTE]

I don't really agree with this since most people either rip or "acquire" .mp3's @ 128kbps - which is, in my opinion, the absolute *minimum* bit rate one should be using.

---

### Post by babel on 2006-05-06
Thanks for the references to the articles everyone.

I will work my way through them & try to get some ideas about playing restricted formats on a Ubuntu system.

---

