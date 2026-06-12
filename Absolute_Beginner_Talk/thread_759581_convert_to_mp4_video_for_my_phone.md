---
title: "convert to mp4 video for my phone"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by niteblind on 2008-04-19
Hi All,

Can someone assist I have been going nuts for a couple of days trying to sort this myself and failing miserbly.

I hvae a training video that I want to put on my nokkia e51 phone as I am going away and it will be the perfect time to watch it. My phone supports mp4 so I am trying to encode to this at 320x240,

The training video I have is a quicktime .mov file so I am not sure if I can convert this or not as I found this script on a link from one of th eposts on this forums as follows:

[https://help.ubuntu.com/community/iPodVideoEncodingL](https://help.ubuntu.com/community/iPodVideoEncodingL)

ffmpeg -i input_file.avi -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec libfaac -ab 192k -s 320x240 -aspect 4:3 output_file.mov

The way I read this it is trying to convert the wrong way for what I want is this correct?

I also tried installing the script mp4ize but this fails every time saying that it cannot find xvid. I have followed lot os links to install about ecery codec I can find so does anyone know if there is something special I need to do for xvid?

If anyone knows  how to put me out of my misery I would be really grateful.

niteblind

---

### Post by niteblind on 2008-04-19
erm bump?

---

### Post by Biggy on 2008-04-19
Download and install   [LIVES]("http://lives.sourceforge.net/index.php?do=downloads&PHPSESSID=909437eb55171119b03af736a7785192")

---

### Post by gambrjl on 2008-04-19
I believe the .mov is just a container.  The command you posted is using the mpeg4 video codec and AAC audio so if you changed it to output_file.mp4 I think it would work.

I don't have ffmpeg built with AAC support so it bombed out when I tried it because of that

---

### Post by niteblind on 2008-04-19
hmmm, yeah i get the same so I tried changing libfaac to liblame and it also bomber and I have that one installed. it seems whatever codec i tell ffmpeg to use it says it cannot find it.

does anyone know why?

niteblind

---

### Post by rkakkar on 2008-04-19
hey.. unfortunately, the best solution for this is nokia's official video converter. see if it works through wine. i tried a lot to find a program to do in it linux but in vain. either the codec doesn't work properly or its too complicated and i'm doing something wrong.

---

### Post by niteblind on 2008-04-19
i didn't nokia provided a video converter. in the short term as i am away in a couple of days that sounds like the best solution do you happen to have a link for it at all?

niteblind

---

