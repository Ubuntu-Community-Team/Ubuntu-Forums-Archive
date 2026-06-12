---
title: "JAR Encoding"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by laginimaineb on 2007-08-10
Hello, I am a Java programmer, and have recently moved to Ubuntu from Windows. I've been working on an application which reads images from JAR files in which they are stored (without compression). When I was working in Windows, I used WinRAR to add the files. Now, however, I am using the default Archive Manager. To my surprise, all images added using the Archive Manager were undetected. I suspect this may be an encoding issue, is there a way to use the same encoding as WinRAR whilst in Ubuntu?

With Thanks,
laginimaineb.

---

### Post by Hospadar on 2007-08-10
you might want to look into 7-zip (I think it's CLI) It's one of the more full featured compressors I know of although I don't know whether or not it could specifically do what you need.

Also you might look into whatever eclipse uses to pack it's jars (it probably does a better job than archive manager).

Another option might be the kde archiver "ark", you can add it with add/remove programs (you don't need to be using kde to use it)

---

### Post by carloslosgrande on 2007-08-10
[FONT="Comic Sans MS"]Hi. Have you looked in 'add/remove applications'?
Click the 'show' box to show 'all available applications' and then search for 'rar'[/FONT]

---

### Post by jw5801 on 2007-08-10
I don't think having rar is the issue since he said he's having an issue with .jar files. Have you got sun java installed on ubuntu? I don't think it comes as default. Either way open up a terminal, firstly type in "jar" (without the quotes) and see what happens. If you have the program installed then that's what you use to pack and extract jars, otherwise entering it into the terminal should tell you what package you need to install to have it. Once you've got it type "man jar" and it should give you the command line options. It might help fix up archive manager too as it'll be the command it runs to extract the jars.

If that doesn't help, check what version of java you're using in Windows and make sure it's the same or higher for linux.

---

### Post by laginimaineb on 2007-08-10
Thanks for your help, but I still can't get it to work. I guess there's something wrong with my code - I'll have to look at that. (I did install 7zip, ark and rar - but they all compress the image rather than store it).

---

### Post by laginimaineb on 2007-08-10
Hey, I'm really sorry to trouble you, problem fixed :D. I was really being stupid, apparently, the program I used did not save the images in the wanted format, they were corrupt.
Thanks for all your help,
laginimaineb.

---

