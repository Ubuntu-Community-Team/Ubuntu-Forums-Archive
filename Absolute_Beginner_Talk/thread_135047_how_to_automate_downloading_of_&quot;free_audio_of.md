---
title: "how to automate downloading of &quot;free audio of the week&quot; from a website"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-02-23
Every week a certain website offers a "free audio download of the week". Is there a way i can automate downolading the file? This audio programme is changed each week, usually on Tuesday. The filename changes each week, but the url of where the week's file is at is always the same ([www.somewebsite.com/audiooftheweek.html)](www.somewebsite.com/audiooftheweek.html)).

But here's some info that may help:

On that webpage, the target audio file is the only one that begins with [FONT="Tahoma"]http://[/FONT] and ends with [FONT="Tahoma"].wma[/FONT]. So if there's a command/script that we can write, this is, I believe, the info we need.


Thanks for the help.
[COLOR="Red"][SIZE="5"]
Update (August 3, 2006): the Website has undergone a change, which makes the scripts break. Please see my latest post ([http://ubuntuforums.org/showpost.php?p=1334321&postcount=23)](http://ubuntuforums.org/showpost.php?p=1334321&postcount=23))[/SIZE][/COLOR]

---

### Post by christhemonkey on 2006-02-23
Maybe as a cron job? (not entirely suer how you do that but someone here will)
```
wget http://somewebsite.com/*.wma
```
Although that probs wont work as you may still get all of the old audio as well. Hmmm!

---

### Post by hanzj on 2006-02-23
Chris,
Well, the old audio is removed when the new audio (the audio of the week) is put up. In other words, only one .wma file will be up at one time.

Hope to hear from others about this.

---

### Post by christhemonkey on 2006-02-23
[https://wiki.ubuntu.com/CronHowto]("https://wiki.ubuntu.com/CronHowto")
Howto use cron.

---

### Post by hanzj on 2006-02-23
[QUOTE=christhemonkey] ```
wget http://somewebsite.com/*.wma
```[/QUOTE]

Are you sure that wget command will work? You see, when I point my browser to http://www.somewebsite.com/audio/, it says
> Directory Listing Denied
This Virtual Directory does not allow contents to be listed.

I tested the wget command. This is what I got

> wget http://www.somewebsite.com/audio/*.wma
Warning: wildcards not supported in HTTP.
--18:38:57--  http://www.somewebsite.com/audio/*.wma
           => `*.wma'
Resolving www.somewebsite.com... 217.34.233.91
Connecting to www.somewebsite.com|217.34.233.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:39:02 ERROR 404: Not Found.

(I changed the real website's url and IP, but when I tried it out, I put in the actual website)

So how can wget work that way? I think that whatever we do, we should somehow have the automated script first go to the html webpage www.somewebsite.com/audiooftheweek.html, then have it do a search for the one and only file on that page that begins with *http:// *and ends with [I].
wma.[/I]. 
I'm no programmer, but this seems to be the way to go about doing it, at least manually.


Thanks.

---

### Post by christhemonkey on 2006-02-23
wget downloads things from a given place (such as your [www.somewebsite.com)](www.somewebsite.com)).
That is, in my understanding.
What is the site you are trying to connect to? Maybe it is not a [http://?](http://?)

---

### Post by steve.horsley on 2006-02-23
Try the attached (untested) script.

Save the script, then edit it, changing line 4 to point to the correct web site.

Edit the permissions to make the file executable (chmod 700 test.py.txt). Rename it if you like. It should dprobably end in .py, but I couldn't upload it with that extension. The run it.

If it works, look at scheduling it to run weekly. I don't see a graphical tool to schedule tasks, so it may be a command line job: **man cron**.

---

### Post by hanzj on 2006-02-23
[QUOTE=christhemonkey]wget downloads things from a given place (such as your [www.somewebsite.com)](www.somewebsite.com)).
That is, in my understanding.
What is the site you are trying to connect to? Maybe it is not a [http://?](http://?) [/QUOTE]

Chris,
Go to [http://www.mlj.org.uk/audio/audioplay.htm](http://www.mlj.org.uk/audio/audioplay.htm), 
In the center of the page, Look fo the text that says 

  > If the above link does not work for you, try **[COLOR="Blue"]here[/COLOR]**

The wget command will work if you know the exact url of the .wma file. For example, this week, the wma file's url is [http://www.mlj.org.uk/audio/streaming/MLJ3196a.wma](http://www.mlj.org.uk/audio/streaming/MLJ3196a.wma). But the thing is, I won't know the url of the future files.There is no set order.

---

### Post by christhemonkey on 2006-02-23
If you do want to schedule it graphically:
```
sudo apt-get gcrontab
```
Or find it in synaptic, its in universe repo.
Or if you prefer KDE there is a kcron in there as well!

I got to go to college now, steve.horsley's script looked fine.

---

### Post by hanzj on 2006-02-23
I downloaded Steve's [test.py.text]("http://ubuntuforums.org/attachment.php?attachmentid=6376&d=1140688413"), opened it in gedit and changed 4th line to http://www.mlj.org.uk/audio/audioplay.htm" I then renamed it to test.py, and in terminal did "chmod 700 test.py".
Then i installed gcrontab from universe and ran it. Then I clicked on the "gcrontab druid" icon, which is located between the X icon and the ? icon(question mark).

On 1st screen, I clicked "next".
On 2nd screen, I clicked "Any Hour", then "Next"
On 3rd screen, I clicked "Some Days of the week" In the "From" dropdown box,  I selected "Wednesday". Then I clicked "Add". Then, "accept". Then clicked "next"
On next screen, I clicked "any month", then clicked "Finish and Set Command"
On the *Command Set* window, I clicked "File" then selected the test.py file i edited. I then clicked "accept."

The gcrontab window looks like this now: [ATTACH]6378[/ATTACH]

Now what do i do next?

---

### Post by christhemonkey on 2006-02-23
If that command works (the test.py) then it should run this every wednesday.

---

### Post by hanzj on 2006-02-23
How do I know if it works? Do I have to keep the gcrontab program running? Where will it place the downloaded file? In my home directory?

Update: Is there a way I can test out the .py file now? To see if the scripting is correct?

---

### Post by hanzj on 2006-02-24
I did "python test.py.txt" (with the correct webpage inserted) and got this printout:

> Traceback (most recent call last):
  File "test.py.txt", line 20, in ?
    u2 = urllib2.urlopen(url2)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 350, in open
    protocol = req.get_type()
AttributeError: 'tuple' object has no attribute 'get_type'


What's wrong?

---

### Post by patrick295767 on 2006-02-24
An easy one is Kcron
```
apt-get install kcron
```
  
vi /etc/crontab
and add root to ur command ... 
and, it'll work fine.
  
Example:
```
 #This file also has a username field, that none of the other crontabs do.
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h dom mon dow user	command
17 * * * *	root	run-parts --report /etc/cron.hourly
# 
25 6 * * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
# 
47 6 * * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
# 
52 6 1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
# Please be informed tthat I am stopping gdm
0,30,55 0,23 * * *	root	/etc/init.d/gdm	stop
# Please be informed tthat I am stopping kdm
0,30,55 0,23 * * *	root	/etc/init.d/kdm	stop
# I start the gdm
0 7 * * *	root	reboot

# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.
```
  
Instead of /etc/init.d/kdm stop
u can replace by it : /etc/init.d/mysupermegascript.sh
(chmod +x /etc/init.d/mysupermegascript.sh)

u can quickly have a look there : [http://www.ubuntuforums.org/showthre...t=64557&page=9](http://www.ubuntuforums.org/showthre...t=64557&page=9)

---

### Post by steve.horsley on 2006-02-27
Sorry for the delay.

Found several bugs, but it seems to work now I have a URL to test against.
Try this version.

Note that the link inside the page is an "mms" URL. If the page you are parsing is different, you may have to change this (line 17) and the length of "mms" (line 23) to suit. Somehoe I think the page you are using is NOT the page I used in my tests.

---

### Post by hanzj on 2006-02-27
Steve, 

On the page I mentioned, there *is* an "mms" url, but there is also a regular http:// wma file that is easily downloadable. Don't click the big  Windows media icon. Rather, please try the simple dark-blue text link below that.
It's the one that says, "  If the above link does not work for you, try  [COLOR="Blue"]**here**[/COLOR]."

Thanks.

---

### Post by hanzj on 2006-03-01
Steve, 
In this post, I'll do 2 things:
1) I'll talk about  the url to this week's audio file
2) I'll say what changes I've made to your 2nd test.py.txt file, with a comment afterwards

------------

Okay, [SIZE="3"]Number 1[/SIZE]. Regarding the link, this week's downloadable wma audio file is [http://www.mlj.org.uk/audio/streaming/MLJ3196b.wma](http://www.mlj.org.uk/audio/streaming/MLJ3196b.wma). 

You thought the url was starting with mms. Perhaps you thought the url was mms://www.mlj.org.uk/audio/streaming/MLJ3196b.wma. That may work with the test.py.txt, but I thought getting an "http://" file will lessen any challenges we may face.


[SIZE="3"]Number 2[/SIZE]
I took a look at your 2nd test.py.txt. 
It has the following:
```
#!/usr/bin/env python

# The url of the main web page
URL = "http://www.mlj.org.uk/audio/audioplay.htm"

import re, urllib2, os


# get the lines from the main page
u1 = urllib2.urlopen(URL)
lines = u1.readlines()
u1.close()

# look for http://<something>.wma
fname = None
for line in lines:
    result = re.search("mms://.*\.wma", line)
    if result:
        url2 = line[result.start():result.end()]
        print 'URL2=', url2
        url3 = "http" + url2[3:]
        print 'URL3=', url3
        u3 = urllib2.urlopen(url3)
        fname = os.path.basename(url3)
        print "Downloading %s..." % fname
        f = open(fname, 'w')
        while True:
            buf = u3.read(2000)
            if not buf:
                break
            f.write(buf)
        f.close()
        u3.close()
        print "Done!"
        break

if not fname:
    print "Didn't find a file name to download, sorry."

```


Below, in color red, is the changes I've made to your line 17:
```
    result = re.search("[COLOR="Red"]http://[/COLOR].*\.wma", line):
```

You said that I may have to change the length of "mms" in line 23, which is:
```
     u3 = urllib2.urlopen(url3)
```

But I don't know if I have to change anything. And if I do, I don't know what to do.

---

### Post by hanzj on 2006-03-01
Hi Steve, i did the python command on my edited vorsion of your 2nd Python file, but i got some problems. But when I ran your file, it worked fine! The file was placed in my home directory! Thanks.

Is there a way to tell the py file to save it in a specific folder in my hard drive, and not at "home" folder. What if I want to save it to, say, home/audio/mlj?

And, how do I make this python file run every Wednesday? Any time is fine. I heard stuff about cron and crontab and gcrontab, but I have no idea about them. Please advise



And a question of secondary importance:
Now that we are clear that we don't have to deal with mms, what changes would you make to the py file, so that it will look for a file that starts with http:// and ends with .wma?


Thanks.

---

### Post by dvarsam on 2006-03-01
I tried to test the script you put above & this is what I got:

root@house:/home/dimitris/Desktop# sh download.sh

download.sh: line 4: URL: command not found
download.sh: line 6: import: command not found
download.sh: line 10: syntax error near unexpected token `('
download.sh: line 10: `u1 = urllib2.urlopen(URL)'

root@house:/home/dimitris/Desktop#


Do you know what is the problem?

What do I have to change?

---

### Post by hanzj on 2006-03-01
dvarsam, 
You tried [Steve's 2nd test.py.txt]("http://ubuntuforums.org/attachment.php?attachmentid=6493&d=1141072538")? It should work without any problems. It worked for me.

---

### Post by dvarsam on 2006-03-01
Yes I tried the version (link) you offered.

And I got this:

root@house:/home/dimitris/Desktop# sh test.py.txt

test.py.txt: line 4: URL: command not found
test.py.txt: line 6: import: command not found
test.py.txt: line 10: syntax error near unexpected token `('
test.py.txt: line 10: `u1 = urllib2.urlopen(URL)'

root@house:/home/dimitris/Desktop#

Steve though says the following:

Note that the link inside the page is an "mms" URL. If the page you are parsing is different, you may have to change this (line 17) and the length of "mms" (line 23) to suit. Somehow I think the page you are using is NOT the page I used in my tests.

Can you tell me what exactly I have to put on those lines to make it work?

Just one example, anything that could make it work...

Thanks

---

### Post by hanzj on 2006-07-12
Hello, 
The webmaster of the site has now changed the layout of the site. The original URL at [http://www.mlj.org.uk/audio/audioplay.htm](http://www.mlj.org.uk/audio/audioplay.htm) gives this message:
> 
Dear Friends,

I apologize if you have missed out on the last few weeks broadcasts, only the way that the weekly program is updated each week has been changed. The program has been going out as usual each week, however this "bookmarked" page is now redundant. 
Had you taken the link from our main home page, all would have been well, so could I urge you to go to our main home page here and then click the "Weekly Broadcast" link, either in the red section near the top of the page, or through the "Audio" menu in the left had pane.


So I edited [Steve's 2nd python script]("http://ubuntuforums.org/attachment.php?attachmentid=6493&d=1141072538"). I changed line 4 from

URL = "http://www.mlj.org.uk/audio/audioplay.htm"

to 

[http://www.mlj.org.uk/audio/radio/index.htm](http://www.mlj.org.uk/audio/radio/index.htm) (let's call it "*Page B*")
But when I tried running the python script, it says "Didn't find a file name to download, sorry."

I realized that "*Page B*" redirects to some other page, which changes every week (Let's call it "*Page Random*"). It's currently at [http://www.mlj.org.uk/audio/radio/2006-7-9.htm](http://www.mlj.org.uk/audio/radio/2006-7-9.htm). 

So how do I automate downloading when the URL (*Page Random*) changes every week? 

Another thing: I wish there was a way that I could be notified that of the status, whether there was a problem, or whether the download was successful. Wish a window could pop up with such a message. Because I assumed that the downloading every week was without any problems, I had missed out on several weeks of audio. The notification in the python script works when I manually run the python script. But in a cron job, I don't see any notifications.

---

### Post by hanzj on 2006-08-03
Hello everybody,
It seems that the free-weekly-audio website  has undergone a change that will break the hard work that we've accomplished up to this point. [http://www.mlj.org.uk/audio/radio/index.htm](http://www.mlj.org.uk/audio/radio/index.htm) will direct to another page
For this week, it redirects to [http://www.mlj.org.uk/audio/radio/2006-7-30.htm](http://www.mlj.org.uk/audio/radio/2006-7-30.htm).

So like before, I have the same desire:

Every time a new "free audio of the week" comes out, I want to have the audio file downloaded into my /spokenword/lloydjones/ folder.

There are 3 audio files available on this page. The one I want to get is the one with the URL starting with http:// and ending in .wma.


This time, I'd like to request an additional thing:
I'd like to get some sort of weekly feedback, every time the command is run, whether the feedback be by email, or by a terminal window popping up. to let me know whether it's succesful, or if there's an error. In the python script that was written up, I could see an error message popping up, but only if I manually ran the script in terminal. When the script is automated, I don't get any such feedback.

---

### Post by harisund on 2006-08-03
Couple of things... I am not much of a coder myself, but definitely a sysadmin and love coming up with small scripts. 

So let's begin our analysis here: 

[http://www.mlj.org.uk/audio/radio/index.htm]("http://www.mlj.org.uk/audio/radio/index.htm")
So we need to start from here, shouldn't we? So that's what I did. Downloaded this webpage and viewed its source. Boy was I stunned. This is what it contained. 

```

 <SCRIPT LANGUAGE="JavaScript">
      5
      6 <!-- Part 'Page of the Week' and Part 'Day of Week Redirection' -->
      7 <!-- Which I have edited to make this display a page every Sunday (1st day of the week) CRMS -->
      8
      9 <!-- Original:  Mark McCain (sub235k@worldnet.att.net) -->
     10
     11 <!-- This script and many more are available free online at -->
     12 <!-- The JavaScript Source!! http://javascript.internet.com -->
     13
     14 <!-- Begin
     15 page_extension = ".htm"; // was html
     16 var today = new Date();
     17 var day = today.getDate();
     18 var month = today.getMonth() + 1;
     19 var year = today.getYear();
     20 if (year < 2000)    // Y2K Fix, Isaac Powell
     21 year = year + 1900; // http://onyx.idbsu.edu/~ipowell
     22 var offset = today.getDay();
     23 var week;
     24
     25 if(offset != 0) {
     26 day = day - offset;
     27 if ( day < 1) {
     28 if ( month == 1) day = 31 + day;
     29 if (month == 2) day = 31 + day;
     30 if (month == 3) {
     31 if (( year == 00) || ( year == 04)) {
     32 day = 29 + day;
     33 }
     34 else {
     35 day = 28 + day;
     36    }
     37 }
     38 if (month == 4) day = 31 + day;
     39 if (month == 5) day = 30 + day;
     40 if (month == 6) day = 31 + day;
     41 if (month == 7) day = 30 + day;
     42 if (month == 8) day = 31 + day;
     43 if (month == 9) day = 31 + day;
     44 if (month == 10) day = 30 + day;
     45 if (month == 11) day = 31 + day;
     46 if (month == 12) day = 30 + day;
     47 if (month == 1) {
     48 month = 12;
     49 year = year - 1;
     50 }
     51 else {
     52 month = month - 1;
     53       }
     54    }
     55 }
     56
     57
     58
     59 week = year+ "-" +  month + "-" + (day); // i.e. 2006-5-16 I've altered this around to have year first CRMS
     60 page = week + page_extension;          // i.e. 2006-5-16.html
     61
     62 link = "<a href='" + page + "'>Page of the Week</a>"; // link to 10-31-99.html
     63
     64 // Line below this was taken from the Day of Week Redirection - CRMS
     65 window.location = "./" + page;
     66 //  End -->
     67 </script>
     68 </head>
     69 <BODY>
     70
     71
     72 <p><center>
     73 <font face="arial, helvetica" size="-2">Free JavaScripts provided<br>
     74 by <a href="http://javascriptsource.com">The JavaScript Source</a></font>
     75 </center><p>
     76
     77 <!-- Script Size:  1.75 KB -->
     78 Did you use this script?  Do you like this site?  Please link to us!
     79 </body>
     80
     81 </html>

```

Smart guys. Real smart. I would have never thought of coming up with a Javascript code to redirect the page. 

Very well, if they can use Javascript we can use our own Bash/python scripts, can't we? :)

With a little bit of common sense and no javascript debugging capabilities, we can see that the webpages are generated on Sundays. 

I am guessing this has to do something with the content, right? (Sorry, I am not Christian :) ). Looking back, there are webpages at the following dates: 
[http://www.mlj.org.uk/audio/radio/2006-7-30.htm](http://www.mlj.org.uk/audio/radio/2006-7-30.htm)
[http://www.mlj.org.uk/audio/radio/2006-7-23.htm](http://www.mlj.org.uk/audio/radio/2006-7-23.htm)
[http://www.mlj.org.uk/audio/radio/2006-7-16.htm](http://www.mlj.org.uk/audio/radio/2006-7-16.htm)
[http://www.mlj.org.uk/audio/radio/2006-7-9.htm](http://www.mlj.org.uk/audio/radio/2006-7-9.htm)
[http://www.mlj.org.uk/audio/radio/2006-6-25.htm](http://www.mlj.org.uk/audio/radio/2006-6-25.htm)
and so on .. 
and the music files in them look like
[http://www.mlj.org.uk/audio/streaming/MLJ1015b.wma](http://www.mlj.org.uk/audio/streaming/MLJ1015b.wma)
[http://www.mlj.org.uk/audio/streaming/MLJ1015a.wma](http://www.mlj.org.uk/audio/streaming/MLJ1015a.wma)
[http://www.mlj.org.uk/audio/streaming/MLJ1011b.wma](http://www.mlj.org.uk/audio/streaming/MLJ1011b.wma)
[http://www.mlj.org.uk/audio/streaming/MLJ1011a.wma](http://www.mlj.org.uk/audio/streaming/MLJ1011a.wma)
[http://www.mlj.org.uk/audio/streaming/MLJ1009a.wma](http://www.mlj.org.uk/audio/streaming/MLJ1009a.wma)

Unfortunately I am not not able to decipher a pattern in the music files. If we had, our quest for the holy grail would have ended right there... but it is not to be ... so we trudge along ... there is a 9a, 11a and 11b, 15a and 15b. I am curious to see some of the future ones .. perhaps we are not lost after all..

Another ray of hope appears in the fact that the source code of all of the above are practically the same, except for one difference. Guess what? Yes indeed, the music file. Here's the corresponding source of the HTML. 

```
<!-- ------------------------------------------------------- Change URL Here ---##################################--------- -->

<A HREF="mms://www.mlj.org.uk/audio/streaming/MLJ1015a.wma"
 ONMOUSEOVER="swapImage(HoverImage,'http://www.mlj.org.uk/images/buttons/playaudiobtn-ovr.gif')"
 ONMOUSEOUT="swapImage(HoverImage,'http://www.mlj.org.uk/images/buttons/playaudiobtn.gif')"><IMG
SRC="http://www.mlj.org.uk/images/buttons/playaudiobtn.gif"
ALT="Click to listen with Windows Media Player" NAME="HoverImage" BORDER="0"
WIDTH="140" HEIGHT="30" ALIGN="ABSMIDDLE"></A>&nbsp;<IMG
SRC="http://www.mlj.org.uk/images/buttons/audioplaywords.gif" WIDTH="325" HEIGHT="30" BORDER="0"
ALIGN="middle"><span lang="en-gb"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
If the above link does not work for you, try <b>
<!-- --------------------------------------------------AND Change URL Here ---##################################--------- -->

<a href="http://www.mlj.org.uk/audio/streaming/MLJ1015a.wma">

<img border="0" src="http://www.mlj.org.uk/images/buttons/here.gif" align="absbottom" width="43" height="13" alt="Try here for a different link, but it 'may not' stream consistently"></a></span>
</TD></TR>
</TABLE>
</CENTER>
<P align="center"></P>
<TABLE WIDTH="60%" ALIGN="CENTER">
<TR>
<TD BGCOLOR="#FFEEDD" ALIGN="CENTER" HEIGHT="40">&nbsp;<SCRIPT>preloadImages("http://www.mlj.org.uk/images/buttons/realaudiobtn-off.gif","http://www.mlj.org.uk/images/buttons/realaudiobtn-ovr.gif")</SCRIPT>


```

Aha! Some progress. 

Consequently, if I were you, here is what I would try and do. 

Download the source code for the corresponding webpage. 

Search for 
```
<!-- --------------------------------------------------AND Change URL Here ---##################################--------- -->
```
Let this occur in line number 'n'. 

Therefore the line number we are interested in is n+1. Somehow strip everything starting from the first " to the second ". This is what follows from a=href tag. 

Then download that. 

As I said, this would require some code .. if somebody can come up with that great. Otherwise, I will give it a shot. 

One thing, this entire procedure assumes the webpage will follow the same format (which I am guessing it does, going back a couple of weeks). If there are any changes, don't worry .. the community here will definitely help reverse-engineer. 

And frankly, I would have expected that website to have provided an RSS feed. If you realize, what we are doing is basically what RSS feeds are meant for ultimately. In today's world of web services what we are doing seems very very primitive. 

So HTML is open source too .....

Hope you had fun :)

---

### Post by harisund on 2006-08-03
Oh sorry, I didn't see the last bit of your post.

About the feedback thing, here's what I would suggest. 

Write up another program which has a database of when what file was downloaded. Make it query the database for a new addition every time you login to your desktop (as in a Auto-Startup program) or put it in your .bashrc. 

And everytime the file is downloaded, update the database.

---

### Post by hanzj on 2006-08-03
> With a little bit of common sense and no javascript debugging capabilities, we can see that the webpages are generated on Sundays.

Yes. On a separate page, they have mentioned that the new audio will be served fresh every Sunday.


> Unfortunately I am not not able to decipher a pattern in the music files. 

I don't think there is much pattern. All I can say is that they split up a recording into two parts, A and B.
Now the numbering is really just the "tape number." I have no idea what they will decide next.

> 
And frankly, I would have expected that website to have provided an RSS feed. If you realize, what we are doing is basically what RSS feeds are meant for ultimately. In today's world of web services what we are doing seems very very primitive.

Well, I think they have their reasons. You see, they don't realy want people to do what I am doing, and that is getting a copy of each file and archiving. They want people to buy these files from their MP3 store. But since I don't have much money to spend for these, and since they are offering it for free legally, why pay at the store? Not to say that they are not worth financially supporting. I think they are.

---

### Post by hanzj on 2006-08-03
> **harisund said:**
> 

Write up another program ...

I don't know how to program. I'm learning, slowly, by example.

---

### Post by harisund on 2006-08-03
Let's give it a try using bash scripts. 

```
echo "http://www.mlj.org.uk/audio/radio/`date +%G-%-m-%-d`.htm" > tempfile

```
This will generate the .htm file for that Sunday. So run it on Sunday nights, after the file gets uploaded. tempfile will contain the correct URL for that week.

```

wget -i tempfile

```
Get the file.

```

mv `date +%G-%-m-%-d`.htm file.htm

```
Just rename the file

```

grep wma file.htm > wmafile

```
This will strip the lines that have .wma in them. 

```

sed -i -e '1d' wmafile

```
This will delete the first line, the one with the mms:// in front

```

sed -i -e 's/<a href=\"//' wmafile
sed -i -e 's/\">//' wmafile

```
This will strip everything except the url of the wma file

```

wget -i wmafile

```

This will get us the wmafile. 

So in effect
```
echo "http://www.mlj.org.uk/audio/radio/`date +%G-%-m-%-d`.htm" > tempfile
wget -i tempfile
mv `date +%G-%-m-%-d`.htm file.htm
grep wma file.htm > wmafile
sed -i -e '1d' wmafile
sed -i -e 's/<a href=\"//' wmafile
sed -i -e 's/\">//' wmafile
wget -i wmafile
rm wmafile
rm tempfile
rm file.htm
rm *.htm
```

Try it out one Sunday, and then put it cron.

Let's check if this works. Then we will figure out a way to notify you of the download. 

Of course, I hope you realize it wouldn't work today or any day except for Sunday. The date command generates a file that is available on the server only if the date matches a Sunday. If you want to test it, manually change the required settings. In other words, everywhere the date appears, just manually type in that command with the correct file. 
That is, for today wherever you see `date....` (including the back-quotes) change it for 2006-7-9

---

### Post by harisund on 2006-08-03
Ok I am assuming that works for you. In the above I simply substitued `date +%G-%-m-%-d` (in 2 lines) for 2006-7-9 and ran the script, it worked just fine. 

Now, let me ponder aloud on a weekly feedback kind of thing. 

1. At the end of the download script, if the download was successful, create a file called 'new-file-added'. Use the touch command
2. Every time you boot your machine, login to GDM or login to the command line, check if 'new-file-added' file exists. If it exists, it means a file has been downloaded. Inform the user of this, and give 2 options. Remind me later, or Ok. 
3. If the user clicks Remind me later, nothing should happen. The whole cycle continue. 
4. If the user clicks OK, delete the file 'new-file-added'. You won't get bothered. 

I am thinking of using Zenity for the same. [Have a look here](http://www.linux.com/article.pl?sid=06/06/28/1932243).

Finally, some housekeeping tasks you might want to do. 

1. You wanted to move the downloaded file to somewhere. That should be as easy as adding a mv statement at the end. 
2. You might want to change the downloaded file name. It will probably download something like MLJ10123.wma or something. Change it to the current date, so that it makes sense when you look at it earlier. You could create an album of these files.

---

### Post by hanzj on 2006-08-04
> **harisund said:**
> 
...

```

wget -i tempfile

```


This is where I got stuck. Terminal gave me this printout:
> 
hanzj@ubuntu:~$ wget -i tempfile
--05:32:50--  [http://www.mlj.org.uk/audio/radio/2006-8-4.htm](http://www.mlj.org.uk/audio/radio/2006-8-4.htm)
           => `2006-8-4.htm'
Resolving [www.mlj.org.uk](www.mlj.org.uk)... 217.64.113.90
Connecting to www.mlj.org.uk|217.64.113.90|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
05:32:51 ERROR 404: Not Found.


I guess this script will only work on Sundays? I just wanted to test it out.

---

### Post by harisund on 2006-08-04
> **harisund said:**
> In the above I simply substitued `date +%G-%-m-%-d` (in 2 lines) for 2006-7-9 and ran the script, it worked just fine.

I did mention I had to change the date. [-X

Naturally, it would work on Sundays only. Because on Sundays the date that gets generated actually corresponds to an existing webpage. What I see is today's date, for which naturally there exists no page. #-o #-o

And again, when testing it on Sunday ensure that the .wma file exists on the server, meaning the MLJ website have updated their website. Likely if you run it Sunday early morning you are going to get another file not found error simply because you try to download something that has not been created yet.

---

### Post by hanzj on 2006-08-04
> **harisund said:**
> 
2. You might want to change the downloaded file name. It will probably download something like MLJ10123.wma or something. Change it to the current date, so that it makes sense when you look at it earlier. You could create an album of these files.


That's a nice idea. I'd probably want to keep the original filetitle.
In other words, an original filename like
MLJ10123a.wma is to be 060706MLJ10123a.wma or060706_10123a.wma (the MLJ part being removed, since all files are from Mr. MLJ anyway).


> **harisund said:**
> 
And again, when testing it on Sunday ensure that the .wma file exists on the server. Likely if you run it Sunday early morning you are going to get another file not found error simply because you try to download something that has not been created yet.


Right. Good point. So, if possible, I'd like to make the script automatically run in the evening time.

---

### Post by hanzj on 2006-08-08
> Unfortunately I am not not able to decipher a pattern in the music files. If we had, our quest for the holy grail would have ended right there... but it is not to be  I am curious to see some of the future ones 

Current URL is  [http://www.mlj.org.uk/audio/radio/2006-8-6.htm](http://www.mlj.org.uk/audio/radio/2006-8-6.htm), and this week's  audio file is 
[http://www.mlj.org.uk/audio/streaming/MLJ3336a.wma](http://www.mlj.org.uk/audio/streaming/MLJ3336a.wma)


I changed the "a" to "b" and got
[http://www.mlj.org.uk/audio/streaming/MLJ3336b.wma](http://www.mlj.org.uk/audio/streaming/MLJ3336b.wma). I was able to do today, without waiting for Sunday, August 13, to come.

---

### Post by harisund on 2006-08-08
How come? I can understand that MLJ-3336a which happened on 2006-8-6 (Sunday). So did it work? Were you able to download at all? I was wondering what happened since there was no post from you at all after Sunday ... 

So I take it that the 'b' doesn't necessarily represent the week after aa?

---

### Post by hanzj on 2006-08-08
> **harisund said:**
> 
So I take it that the 'b' doesn't necessarily represent the week after a?

On the contrary. B always comes after the A part. This  is how I was able to "predict" and download next week's sermon.

---

### Post by hanzj on 2006-08-08
Harisund,
Today, I ran the step-by-step process manually, making the change from `date ...` to today's date and my computer was able to download the wma file.


So I'm guessing that the bash script (the one with the `date ...`) will work. 

What is the next step?

So how exactly do i make a bash script?

---

### Post by harisund on 2006-08-08
->> type out all the commands sequentially in a file, name it 'sermon-download'
->> If required substitute the manually entered date with the `date -...` command enclosed within backticks. 
->> This sequence of commands in a file makes the script. In order to succesffully run it, change its permissions. Execute 'chmod +x sermon-download'. From that point on, you can run it by executing /path-to-file/sermon-download. Typically, if you have created the file in your home directory, you would run /home/hanzj/sermon-download. Or if you have it in your bin sub directory you would execute /home/hanzj/bin/sermon-download
->> On executing it, each command in that file will be executed one after the other. Hopefully there should be no errors. Right now I do not have any sort of error checking in there. So if something bombs, you will have to manually figure out what went wrong. 

Then you can go ahead and add the entire executable (/home/hanzj/bin/sermon-download) in your crontab appropriately.

---

### Post by hanzj on 2006-08-09
harisund,
thanks. did as you said. 

17 4 * * 7 /home/hanzj/sermon-download

[COLOR="White"][SIZE="1"]to get feedback, you should have the script mail you a report. Alternately, if your system is configured with a local emailer, then any output that your script echo's will get emailed to you (cron perceives any text printed by a job to be an error so it emails you about it

 the significance of knowing it's location is (1) learning more about Linux (2) realizing that it's *not* in your home directory and this is *exactly* why I instructed you to create a copy in ~/.crontab instead of just using crontab -e . If you maintain the practice of always managing your crontab file from ~/.crontab and then uploading it to the spool directory, you'll be sure to always have a private copy[

from: josh_. 
create a directory called "/log"
then in your crontab add 2>&1 entry at the end of your entry. so something like this. "00 4 * * * * /script/whatever > /output/whatever 2&>1. 
that would run whatever script, when you want it to, then write an output file for that script everytime it runs giving you the errors and anything you "echo" in the script itself. then you wont have to setup the smtp and all that other stuff...

you can use */5 rather than 5,10,15,etc.


[/SIZE]
[/COLOR]

---

### Post by harisund on 2006-08-09
Hmmm.... now we wait and watch :)

---

### Post by hanzj on 2006-08-09
I added this entry into my .crontab

17 4 * * 7 /home/hanzj/documents/sermon-download >> /home/hanzj/log/sermon-download 2>&1. 

It will collect the weekly logs.

---

### Post by hanzj on 2006-08-09
how can we get the script to download the wma file into /home/hanzj/audio/spokenword/lloydjones
?

---

### Post by harisund on 2006-08-09
I am not sure if that would work. Have a try though. 

If it doesn't we will create some kind of logging within our script itself. 

What about the feedback / remainder thing you were talking about?

---

### Post by hanzj on 2006-08-09
Post 40 will give me feedback, but it will not be pushed to my face. Rather the feedback will be kept in a log.

If it's too hard to get the weekly feedback to "pop up" to my face", then i won't bother.

---

### Post by hanzj on 2006-08-09
harisund, 
another person suggested the following to be the sermon-download script
```

#!/bin/sh

# set current directory to save us having to specify absolute paths:
cd /home/hanzj/documents

# define some variables so we don't have to specify long names repeatedly:
f2=wma-filename
f1=`date +%G-%-m-%-d`.htm  # the extra dashes prevent padding with 0s.

# If the user specified a date on the command line, then use that one instead:
# (useful for testing or manually getting last week's sermon)
case $1 in ?*)
  f1=$1.htm
esac

# download the webpage containing the desired URL:
# (if wget exits with error, set variable $error to 1).
wget http://www.mlj.org.uk/audio/radio/$f1  || error=1

# extract the sermon URL from the webpage we downloaded:
# The page contains two references to the .wma file.  Just use the first one.
sed -n '/href.*wma/{s/.*<a href="//; s/">.*//p; q}'  $f1 >$f2

# download the sermon itself:
wget -i $f2  || error=1

# remove the temporary files we created:
rm -f $f1 $f2

# Set a user-friendly message depending on the value of $error:
case $error in
  '') msg='weekly sermon download ok' ;;
  1) msg='weekly sermon download failed' ;;
esac

# report success or failure:
xmessage "$msg" &
```

---

### Post by harisund on 2006-08-09
You could just add 'mv *.wma /home/hanzj/audio/spokenword/lloydjones' at the end of your script. 

About the feedback thing, no it's not hard. But it would require some thinking and coding. Will get back to you later on that :)

---

### Post by harisund on 2006-08-09
Oh, I was just reading the script that you had posted. 

Yeah .. that's fine too... just that it is more polished a script that mine. I haven't spent enough time on the script, and just randomly threw in some commands and made a rag-tag script, while the person who gave you this script obviously spent more time. So you should be able to use that and you will be fine. Besides, from what I see the only difference is in the sed command and the way the error is handled (I of course didn't even bother for the error).

---

### Post by hanzj on 2006-08-14
I checked sermon-download.log and here's what it says:

> --17:26:02--  [http://www.mlj.org.uk/audio/radio/2006-08-13.htm](http://www.mlj.org.uk/audio/radio/2006-08-13.htm)
           => `2006-08-13.htm'
Resolving [www.mlj.org.uk](www.mlj.org.uk)... 217.64.113.90
Connecting to www.mlj.org.uk|217.64.113.90|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:26:02 ERROR 404: Not Found.

sed: can't read 2006-08-13.htm: No such file or directory
No URLs found in wmafile.
Error: Can't open display: 


---

### Post by harisund on 2006-08-14
The problem is somewhere you have copied the script wrong. 

You are generating a date of 2006-08-13 while the actual string should have been 2006-8-13. 

Check if you have 'f1=`date +%G-%-m-%-d`.htm 
correctly. I am guessing you missed a '-' before the 'm'

---

### Post by hanzj on 2006-08-14
My sermon-download had:
f1=`date +%G-%m-%d`.htm

So i added a hyphen before 'm' and it is now
f1=`date +%G-%-m-%d`.htm

should there be a hyphen before 'd', too, so that it looks like:
f1=`date +%G-%-m-%-d`.htm
?

---

### Post by harisund on 2006-08-14
If you look at the original script provided by the other person, you will find a line that goes 

> f1=`date +%G-%-m-%-d`.htm  # the extra dashes prevent padding with 0s.

So yes, you will naturally need the extra dashes.

How did you create the script? If you had blindy copied and pasted those hyphens would have come along anyway. Perhaps you tried to type them out and missed something along the way?

---

### Post by ic56 on 2006-08-14
> I checked the sermon-download.log. This is what it said:

Mmmm yes.  I see the problem.  Read on; there's a surprise
solution at the end.  For those joining us lately, the
script in question was posted a couple messages earlier
in this thread.  An updated version is posted at the end.

Let's walk through the error log.  It begins with output
from the wget utility, which is used to download ("get")
files from the (W)orld Wide Web.

First, wget reports the URL it intends to download, and also
the filename into which it will try to save the file:

```

> --17:26:02--  [http://www.mlj.org.uk/audio/radio/2006-08-13.htm](http://www.mlj.org.uk/audio/radio/2006-08-13.htm)
>            => `2006-08-13.htm'

```

Next, wget needs to figure out the numeric address of the
web server on which the file is located.  That's called an
IP address (IP = Internet Protocol).

To do this, it must contact a DNS server (DNS = Domain Name
Service), give it the desired webserver's name
([www.mlj.org.uk](www.mlj.org.uk)) and, hopefully, if the DNS server (aka name
server) knows the answer, wget will receive back the
webserver's IP address.

If the name server doesn't know the answer, it might suggest
another who might.  Thus, name resolution can take several
connections to several servers.  It can be a lot of work if
you try to do it manually, but the messages exchanged are
terse and so it doesn't take much bandwidth.  You usually
get an answer within a second.

The process is called "name resolution".  The collective of
all the name servers and all the backend software used to
access them is referred to as DNS, aka the name service.

wget isn't bothering to tell us which name server(s) it
contacted, and all the details of what transpired, but it
inform us (a) when it's about to begin the process, and (b)
when it's done, it reports the final answer:

> Resolving [www.mlj.org.uk](www.mlj.org.uk)... 217.64.113.90

In this case, the name service was successful in resolving
our webserver's name and wget reported the answer (217...).

Now, wget tries to open a connection to the webserver, using
its IP address.  Apparently, that went ok too:

> Connecting to www.mlj.org.uk|217.64.113.90|:80... connected.

Next, wget reports that it spoke to the webserver over the
opened connection, and told the webserver which file it
wants to download -- that's called an HTTP request
(HyperText Transfer Protocol).

Webpages are called "hypertext" because they can contain
links to other webpages.  Someone coined the word a couple
of decades ago.  "hyper" is Greek for "super-duper" :-).

Anyway, wget reports the webserver's response -- an error 404:

> HTTP request sent, awaiting response... 404 Not Found

There's two or three responses that webservers often send
back to clients; the errors all begin with 400.  The 404
error is the most common; it means there's no such file on
the webserver.  "200 OK" would have been the webserver's
answer for a successful download.  For a quick list of the
other error codes and related neat stuff, check out this
webpage:

```

  http://AWstats.sourceForge.net/docs/awstats_glossary.htm

```

Finally, in case we weren't paying attention, wget
summarizes for us what happened.  At 5:26 pm, it received a
404 (wow! really? :-) ):

> 17:26:02 ERROR 404: Not Found.

So it looks as if there was no sermon posted on the website
for that day.  Bummer!  :-(

The script then continues.  The next command is "sed" (the
Stream EDitor -- so named because it is designed to work one
line at a time, on a stream of incoming text).  And sed
complains that the file which wget was supposed to download
doesn't exist:

> sed: can't read 2006-08-13.htm: No such file or directory

Well, that's not a surprise :-) ...but it can be misleading.

It would be nice if the script stopped when wget failed.
There are several ways to do this.  To get started on the
way to improving the script, read the bash manpage (on the
command line, type "man bash", without the double quotes).

That manpage is long but you don't need to read all of it.
Just look for the definition of the "$?" variable, the
"case" command, the "||" construct, and the "-e" flag.
That's enough knowledge to figure out 3 separate ways of
achieving error handling in the script (each method has pros
and cons; since you're a beginner, pick whichever you find
easiest).

Let's go on.  The next message doesn't say who it's from
(bad bad bad).  But we can guess:

> No URLs found in wmafile.

Hmmm, what program called by our little script comes after
the sed command and would know about URLs?  Well, there's a
wget right after the sed -- "wget -i".  The "-i" flag tells
wget to look for the URL inside a file, rather than getting
it from the command line.  Now the error makes sense: since
the earlier stuff failed, the file, in which the "wget -i"
is looking, doesn't contain a URL.


Let's review.  The first wget was supposed to download a
page that contains (buried inside lots of other text), the
URL of the page we actually want.  Then, sed was supposed to
extract that URL, and store it into a second file.  Finally,
our second wget was supposed to download the page whose URL
would have been in the file produced by sed.

What actually happened is that the first wget failed (error
404).  sed complained about its input file being absent but,
because of the way that this script is coded, an (empty)
file was created anyway.  So the 2nd wget sees the file but
doesn't find anything inside it.  Hence "No URLs found in
<filename>".


Now, on to the last line in the logfile:

> Error: Can't open display:

Sadly, the program reporting the error isn't reporting its
own name :-( but the message contains a clue: "display" is
X's jargon for your PC's monitor (X is the name of Linux's
GUI windowing system.  Don't blame me;  It was named by the
MIT folks who wrote it).

There's only one program in this script that knows about
GUIs -- xmessage.  A clue is that the command's name begins
with "x", though not all X programs are named that way --
only the ones from the early days.  xmessage is a simple
little program that displays a window on your monitor with
the text you supply on the command line.

Anyway, unless you've seen this error before, you wouldn't
know what's going on but it's a common problem.  In this
case, it's caused by a bug in the script: the $DISPLAY
environment variable isn't set and thus xmessage doesn't
know where your PC's monitor is.

The program isn't being pedantic or silly: X applications
can display to the monitor of any remote PC on the Internet
(if that PC runs X, and if the computer's owner permits it).
Besides, fancier computers often have multiple monitors.

If you run the script manually, you won't get this problem,
because the DISPLAY environment variable gets defined into
your window manager when you login through the GUI.  Any
programs you start from the GUI inherit it.  This includes
any shells (terminal windows) you start from the GUI and any
applications you start from those shells, etc, etc.

But, when you run the script from cron (the system daemon
used to run programs at odd hours in the night), cron hasn't
logged in through your GUI (!) and it doesn't have your
environment variables, so these variables aren't there for
the script to inherit.

The quick fix is to modify the line in the script to read
like so:

```

  DISPLAY=:0.0  xmessage "$msg" &

```

That sets the environment variable DISPLAY in xmessage's
environment space.  We are hardcoding it to :0.0 which is a
shorthand for specifying the local computer (":" with no
hostname before it), at video card 0 (your only video card),
at monitor 0 (your only monitor)

Some video cards have connectors for multiple monitors; some
video cards can co-exist with others inside a single
computer.  It all amounts to the possibility of a wall of
monitors all controlled by one kick-*** computer!  Most
people can't afford that kind of hardware but, hey, our
software is ready! :-)


All right, so how come there was no sermon last Sunday?
Could it be that the website changed the filename?  I ran
wget manually a few times.  First, I tried to get a listing
of the files in that directory:

```

  $ wget http://www.mlj.org.uk/audio/radio/

  --14:44:22--  http://www.mlj.org.uk/audio/radio/
             => `index.html'
  Resolving www.mlj.org.uk... 217.64.113.90
  Connecting to www.mlj.org.uk[217.64.113.90]:80... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 2,068 [text/html]

  100%[===========================================>] 2,068 --.--K/s

  14:44:32 (19.72 MB/s) - `index.html' saved [2068/2068]

```

So the parent directory of the file exists, but when we
request it, the webserver gives us instead the index.html
file contained in that directory.

That's the default behaviour of webservers: if an index.html
file exists, the webserver will give you that file instead
of a directory listing.  This is both a convenience and also
a primitive form of security: you can only learn what files
are available by following links and looking for hints in
the index.html file.

Next, I tried getting the actual file we wanted, using last
Sunday's date, which I cut and pasted from the wget error
message in the error log you posted:

```

  $ wget http://www.mlj.org.uk/audio/radio/2006-08-13.htm

  --14:46:17--
  http://www.mlj.org.uk/audio/radio/2006-08-13.htm
             => `20060-08-13.htm'
  Resolving www.mlj.org.uk... 217.64.113.90
  Connecting to www.mlj.org.uk[217.64.113.90]:80... connected.
  HTTP request sent, awaiting response... 404 Not Found
  14:46:18 ERROR 404: Not Found.

```

Yup, sure enough there's no such file.

But, wait a minute.  I recall from our private discussion
when I was last modifying that script, that the filenames on
the webserver were supposed to have dates *without* leading
zeros.  The script makes sure they're generated that way by
using "%-" instead of just "%", throughout the date command.
Weird...  Let's try downloading the *correct* filename, as
I recall it from our discussion, to see if it's there:

```

  $ wget http://www.mlj.org.uk/audio/radio/2006-8-13.htm  # -8- instead of -08-

  --14:46:25-- http://www.mlj.org.uk/audio/radio/2006-8-13.htm
             => `2006-8-13.htm'
  Resolving www.mlj.org.uk... 217.64.113.90
  Connecting to www.mlj.org.uk[217.64.113.90]:80... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 31,974 [text/html]

  100%[===========================================>] 31,974   96.03K/s

  14:46:31 (95.93 KB/s) - `2006-8-13.htm' saved [31974/31974]

```

Wow!  There *is* a sermon posted for last Sunday!

So how come the script produced a differently formatted
date?  Let's run the script to watch it break.

First, I had to modify my copy of the script to "cd" to a
place suitable on my system (/home/ic/tmp rather than
/home/hanzj/documents).  Then, I invoked it, giving it last
Sunday's date, rather than letting it default to today's
date.  Like so:

```

  $ sh ~/examples/weekly-url-download.sh 2006-8-13

  --16:54:26-- http://www.mlj.org.uk/audio/radio/2006-8-13.htm
             => `2006-8-13.htm.2'
  Resolving www.mlj.org.uk... 217.64.113.90
  Connecting to www.mlj.org.uk[217.64.113.90]:80... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 31,974 [text/html]

  100%[===========================================>] 31,974 96.05K/s

  16:54:27 (95.86 KB/s) - `2006-8-13.htm.2' saved
  [31974/31974]

  --16:54:27-- http://www.mlj.org.uk/audio/streaming/MLJ3336b.wma
             => `MLJ3336b.wma'
  Resolving www.mlj.org.uk... 217.64.113.90
  Connecting to www.mlj.org.uk[217.64.113.90]:80... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 7,141,352 [audio/x-ms-wma]

  100%[======================================>] 7,141,352 370.54K/s ETA 00:00

  16:54:55 (259.05 KB/s) - `MLJ3336b.wma' saved
  [7141352/7141352]

  FINISHED --16:54:55--
  Downloaded: 7,141,352 bytes in 1 files

```

Huh!  The script worked!  And, boy, that's a big download!

So, what gives?  Looking more carefully at the logfile you
supplied, I noticed another inconsistency between the
logfile output you posted and what the code in the posted
script does.  Look again at this line from your logfile:

> No URLs found in wmafile.

"wmafile"?!  That's what the filename to which the old
version of the script wrote the URL.  The latest version
writes the URL to "wma-filename".  Dude!  You're not using
the script that you posted!  You're using using the older
one that was posted several messages ago.

Come to think of it, a better name for that file might be
"wma.url" since it's intended to contain a full URL to a
.wma file, not just its filename.  Here's an updated copy of
the script with all the changes:

```

#!/bin/sh

# set current directory to save us having to specify absolute paths:
cd /home/jeff/documents

# define some variables so we don't have to specify long names repeatedly:
f2=wma.url
f1=`date +%G-%-m-%-d`.htm  # the extra dashes prevent padding with 0s.

# If the user specified a date on the command line, then use that one instead:
# (useful for testing or manually getting last week's sermon)
case $1 in ?*)
  f1=$1.htm
esac

# download the webpage containing the desired URL:
# (if wget exits with error, set variable $error to 1).
wget http://www.mlj.org.uk/audio/radio/$f1  || error=1

# extract the sermon URL from the webpage we downloaded:
# The page contains two references to the .wma file.  Just use the first one.
sed -n '/href.*wma/{s/.*<a href="//; s/">.*//p; q}'  $f1 >$f2

# download the sermon itself:
wget -i $f2  || error=1

# remove the temporary files we created:
rm -f $f1 $f2

# Set a user-friendly message depending on the value of $error:
case $error in
  '') msg='weekly sermon download ok' ;;
  1) msg='weekly sermon download failed' ;;
esac

# report success or failure:
DISPLAY=:0.0  xmessage "$msg" &

```


And that concludes today's lesson!

Happy hacking!
-ic

---

### Post by harisund on 2006-08-14
And I thought I was the one who wrote lenghty posts.

---

### Post by hanzj on 2006-08-15
ic56.
Welcome to UbuntuForums. And thanks for your post, your very first post on the UbuntuForums.  It's high-quality. Your contribution is much appreciated.

> **ic56 said:**
> 
And that concludes today's lesson!
Happy hacking!
You make  learning about hacking (er, linux) a fun thing. Thank you, teacher!

---

### Post by hanzj on 2006-10-09
ic, or to any other kind and knowledgeable person,

On Sunday, October 8, 2006, The dialog window said that "Download failed." This may be because the link cannot be found anymore. I can download the audio manually, however. What's wrong?

---

