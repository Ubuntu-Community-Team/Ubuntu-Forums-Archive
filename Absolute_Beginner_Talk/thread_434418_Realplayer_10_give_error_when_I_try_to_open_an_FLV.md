---
title: "Realplayer 10 give error when I try to open an FLV file"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by peter_from_hobart on 2007-05-05
Hello,

This is Peter E Williams here. I'm a NEWBIE at using UBUNTU.

I am attempting to play a .FLV file with Realplayer 10. 

I get the error message:

The player does not have the capabilities to play this content.

The following components are required: FLV

URL: file:///media/hda5/My Documents/My Videos/Kermit & Debbie Harry sing The Rainbow Connection.flv

The file is an .FLV file of the Muppet Kermit the Frog and Debbie Harry (lead singer of the Rock Band Blondie) singing The Rainbow Connection. As far as I'm aware the FLV file is okay. { I used to love to play this FLV file when I my computer had the Windows XP Home Edition Operating System} Now my computer is 100% UBUNTU 6.10 LTS. 

Can someone please help me. I figure that I need to install the FLV component but I don't understand how. 

I have a mental illness so I try not to get upset when my computer is not working.

I will be pleased to provide any info to anyone who would like to help me.

Also please note that last time I checked I could not send emails using the Evolution email client program.

I can browse the internet fine & last time I checked I could receive emails using my GMAIL email account. My  gmail email is: [email]pewtas@gmail.com[/email]

I hope that I have provided sufficient info. 

Yours Sincerely & with Best Wishes
Peter_from_Hobart

Peter Eric (aka 'pew') WILLIAMS

-----------------------------------------------------

---

### Post by dunedust on 2007-05-06
I use mplayer to play flv files
It works quite well

You can get mplayer from the repositories

```
sudo apt-get install mplayer
```

Else you can convert the flv file to an mpg and play it using any media player
for this you will need to install ffmpeg

```
sudo apt-get install ffmpeg
```

To convert your flv file use

```
ffmpeg -i a.flv -ab 56 -ar 22050 -b 500 -s 240x180 a.mpg
```

where 'a' is your filename

If you are not comfortable using the command line you can use this script

[http://ubuntuforums.org/showthread.php?t=255992](http://ubuntuforums.org/showthread.php?t=255992)

---

### Post by peter_from_hobart on 2007-05-06
Dear Wonderful people at the UBUNTU Forums

Thank you so very much for helping me. Even tho' I do not like to use the "Konsole" to enter commands, I did so.

I used the following code:

Code:
---------
ffmpeg -i kermit.flv -ab 56 -ar 22050 -b 500 -s 240x180 kermit.mpg

---------

And to my great happiness and surprise it worked!!! I wrote the command from my email onto a piece of paper and then I opened an Application / System Tools / Konsole and eventually I realized that my file was in the 'Desktop' (spelt with a capital D). And I carefully entered the command (see above). And it worked!!!!!!!!!!

Thank you all very much. *** BIG SMILE ***

Now I can play my favourite MPEG file which I think is very good!!! It is a wonderful video with sound of the Muppet Kermit the Frog and Debbie Harry (lead singer from the Rock Band 'Blondie') singing "The Rainbow Connection". I think that it was recorded in about 1981. I found this file somewhere on the internet and I have a number of .FLV files (whatever they are) of different ppl singing that song. But Kermit the Frog & Debbie Harry are my favourite!!!!

Please also pass on my thanks to the creator of the Totem 1.4.3 Movie Player. Actually I want to thank all of the people at UBUNTU. You are all so very clever and talented.

Yours Sincerely and With Best Wishes,
pew { poet }

My totally free website is:
[http://pewtas.googlepages.com](http://pewtas.googlepages.com)   (please check it out and tell you friends about it)
- Show quoted text -



On 07/05/07, Ubuntu Forums <site@ubuntuforums.org> wrote:
- Show quoted text -

    Dear peter_from_hobart,

    You are subscribed to the thread "Realplayer 10 give error when I try to open an FLV file" by peter_from_hobart, there have been 2 post(s) to this thread, the last poster was dunedust.
    [http://ubuntuforums.org/showthread.php?t=434418](http://ubuntuforums.org/showthread.php?t=434418)

    These following posts were made to the thread:
    ************
    Realplayer 10 give error when I try to open an FLV file
    [http://ubuntuforums.org/showthread.php?p=2600902#post2600902](http://ubuntuforums.org/showthread.php?p=2600902#post2600902)
    Posted by: peter_from_hobart
    On: May 6th, 2007 01:26 PM

    Hello,

    This is Peter E Williams here. I'm a NEWBIE at using UBUNTU.

    I am attempting to play a .FLV file with Realplayer 10.

    I get the error message:

    The player does not have the capabilities to play this content.

    The following components are required: FLV

    URL: file:///media/hda5/My Documents/My Videos/Kermit & Debbie Harry sing The Rainbow Connection.flv

    The file is an .FLV file of the Muppet Kermit the Frog and Debbie Harry (lead singer of the Rock Band Blondie) singing The Rainbow Connection. As far as I'm aware the FLV file is okay. { I used to love to play this FLV file when I my computer had the Windows XP Home Edition Operating System} Now my computer is 100% UBUNTU 6.10 LTS.

    Can someone please help me. I figure that I need to install the FLV component but I don't understand how.

    I have a mental illness so I try not to get upset when my computer is not working.

    I will be pleased to provide any info to anyone who would like to help me.

    Also please note that last time I checked I could not send emails using the Evolution email client program.

    I can browse the internet fine & last time I checked I could receive emails using my GMAIL email account. My  gmail email is: [email]pewtas@gmail.com[/email]

    I hope that I have provided sufficient info.

    Yours Sincerely & with Best Wishes
    Peter_from_Hobart

    Peter Eric (aka 'pew') WILLIAMS

    -----------------------------------------------------
    ************
    Re: Realplayer 10 give error when I try to open an FLV file
    [http://ubuntuforums.org/showthread.php?p=2601036#post2601036](http://ubuntuforums.org/showthread.php?p=2601036#post2601036)
    Posted by: dunedust
    On: May 6th, 2007 02:05 PM

    I use mplayer to play flv files
    It works quite well

    You can get mplayer from the repositories


    Code:
    ---------
    sudo apt-get install mplayer
    ---------
    Else you can convert the flv file to an mpg and play it using any media player
    for this you will need to install ffmpeg


    Code:
    ---------
    sudo apt-get install ffmpeg
    ---------
    To convert your flv file use


    Code:
    ---------
    ffmpeg -i a.flv -ab 56 -ar 22050 -b 500 -s 240x180 a.mpg
    ---------
    where 'a' is your filename

    If you are not comfortable using the command line you can use this script

    [http://ubuntuforums.org/showthread.php?t=255992](http://ubuntuforums.org/showthread.php?t=255992)


    All the best,
    Ubuntu Forums

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    Unsubscription information:

    To unsubscribe from this thread, please visit this page:
    [http://ubuntuforums.org/subscription.php?do=removesubscription&type=thread&subscriptionid=444342&auth=cd9979d8fb1030c57a77e368178ebe61](http://ubuntuforums.org/subscription.php?do=removesubscription&type=thread&subscriptionid=444342&auth=cd9979d8fb1030c57a77e368178ebe61)




-- 
Fond Regards,
Peter Eric (aka 'pew') WILLIAMS

My free website is:
[http://pewtas.googlepages.com](http://pewtas.googlepages.com)

(please visit my free website and let me know what you think about it.)

---

