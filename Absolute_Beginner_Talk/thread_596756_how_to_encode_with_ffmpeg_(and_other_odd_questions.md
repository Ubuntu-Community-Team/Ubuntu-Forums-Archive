---
title: "how to encode with ffmpeg (and other odd questions)"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-10-29
Greeting all (again),
Ok, I think I have things working outsmoothly. I get some odd freezes on my system when I but I think that is to be expected (usually why I am trying to install something).

Anywho, I am trying to figure out how to convert an avi file to mp4 using ffmpeg.  I am so completely new to linux that I feel like I need training wheels in order to go anywhere, so any help would be greatly appreciated.

Thanks

---

### Post by juantovarm on 2007-10-30
ffmpeg is a very nice tool to use, you can do a lot of stuff, 
basically what you have is [inputfile options] [input file] [output file options] [output file]
imagine the name of file is earth.avi
then
ffmpeg -i earth.avi -ab 128 -b1500kb/s earth.m4v

the "ab" option is audio bit, it is preconfigured at 64 with is really bad, so i put it at 128 because i like that one. the "b" option is video rate, it comes preconfigured at 200, which is really low. The "-i" flag is VERY important, you are telling ffmpeg which is your input file, if you don't typw it it, you'll modify your original video

when i put the output extension to mp4 i get an error, that could be my box though, i'm not sure and i don't know if mp4=mpeg4; but i do know that mpeg4=m4v

Hope it helps

---

### Post by mangurt on 2007-10-30
Sorry for the delay in responding, that does explain stuff, now my only question is do I have to be in the folder where the file is located (is /user/video ) or is it just fine to type out the command line in terminal?  Sorry for the nOOb questions, but I am still trying to learn my way around linux (switched from windows a few days ago, and not looking back)
Thanks again!

---

### Post by juantovarm on 2007-10-30
you have to be on the folder where your video is, or tell ffmpeg the route to the video, but that's too much of a hassle, so, it's better to be there. 

I switched not so long ago, maybe one and a half years ago, and have never had the need to use windows, and i just fell in love with the command line specially with ffmpeg. 

So, congratulations on your switch and don't hessitate to ask all the questions you need, you'll learn like that and will be able to help others as well. 

Remember that every application under linux has a man page, it is a very useful tool, to invoke it just type in ther terminal: man nameofapplication eg. man ffmpeg

I hope you enjoy your experience :popcorn:

Juan


you should check the page [www.linux.org/lessons/](www.linux.org/lessons/)  the have quite a bit of information that i found to be very useful

---

### Post by mangurt on 2007-10-30
Ok, I have to be in the folder, so that means I have to change directories in the terminal?  Hmm...I will have to search around to find out how to do that.  I started looking at the guide, and wow, I wish I would have looked at that before, but I am like the normal "male" I don't need directions to put an entertainment center together (my dog is really happy with his new dog-house, and the TV is still on the floor) :)

---

### Post by juantovarm on 2007-10-30
Be smart and don't be lazy, READ and STUDY it makes a world of difference

[http://www.linux.org/lessons/beginner/l4/lesson4b.html](http://www.linux.org/lessons/beginner/l4/lesson4b.html)

---

