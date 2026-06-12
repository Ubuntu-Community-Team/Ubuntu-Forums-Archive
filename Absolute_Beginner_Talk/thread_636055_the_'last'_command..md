---
title: "the 'last' command."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Royal_Pwner on 2007-12-09
I just got an ubuntu computer. I need to monitor the amount of time spent on the computer on a daily basis. I'm doing this using the 'last' command in the terminal. However, I don't know how to interpret the results. Could someone help me? Here are some results. (screenie attached.)

---

### Post by akopacsi on 2007-12-09
Would you post an output here? I'd like to help, but I am using Windows at the moment.

---

### Post by akopacsi on 2007-12-09
Oh, sorry I didn't see the attached image... 8-)
It's clear that the lines including the word "reboot" display the times when you started your computer.
I guess you are interested in the length of your own sessions, so it's better to filer this output. You can use the command "grep" to do it:
last | grep hereisyourname
So now you can see the date and time values when you logged in and out.
The values tty0 and others tell you the number of terminal you used. They're not too exciting when you are the only user on the computer, there's nothing to do with them. The last column contains the most important information, they display the lenght of user sessions in hour:minute format. I wonder if there's a way to sum up them... maybe.

---

### Post by Royal_Pwner on 2007-12-09
Yeah. I need to find a way to sum up the amount of time on the computer by day.
Without paying money.
 
Thanks for the help.

---

### Post by Krydahl on 2007-12-09
Shouldn't be hard to write a script - at least if your interested in how long you left yourself logged in at the computer as opposed to the time you were actually using it.

Pipe the output through grep, looking for tty7, use sed or awk to pull out the entry in the last column, add them up, covert the minutes into hours.

---

### Post by Royal_Pwner on 2007-12-09
But I need real time, not cpu time.
Does the last command print out cpu time or real time?
And I'm a noob, so could you explain what you meant in that last line?

---

### Post by benson444 on 2007-12-09
Maybe the ac command is what you're after? Check out these links:

[http://articles.techrepublic.com.com/5100-6345-1053302.html](http://articles.techrepublic.com.com/5100-6345-1053302.html)

[http://www.computerhope.com/unix/uac.htm](http://www.computerhope.com/unix/uac.htm)

---

### Post by Royal_Pwner on 2007-12-09
Benson is now officially one of the best people ever.
That's *exactly* what I needed.

---

### Post by benson444 on 2007-12-09
Actually, I'm not sure it's exactly what you needed...

I've just been playing around and it seems that ac totals up all of your logins. If you open a terminal and enter the command 'top' you'll see the number of users on the first line. Now open another terminal and you'll see the users increase by one. It'll increase by one for each new terminal you open because you are logging in to a separate shell. Press q to exit top.

I just ran last and ac and have this

~$ last
pts/0        :0.0             Sun Dec  9 21:00   still logged in   
pts/1        :0.0             Sun Dec  9 20:55 - 20:55  (00:00)    
pts/0        :0.0             Sun Dec  9 20:54 - 20:57  (00:03)    
pts/1        :0.0             Sun Dec  9 20:31 - 20:31  (00:00)    
pts/0        :0.0             Sun Dec  9 20:27 - 20:47  (00:19)    
pts/0        :0.0             Sun Dec  9 20:23 - 20:23  (00:00)    
pts/0        :0.0             Sun Dec  9 20:18 - 20:20  (00:01)    
tty7         :0               Sun Dec  9 20:18   still logged in
.
.
~$ ac -d
Dec  1	total        3.41
Dec  2	total       19.08
Dec  3	total        3.89
Dec  4	total       16.28
Dec  5	total       13.95
Dec  6	total       10.81
Dec  7	total       11.03
Dec  8	total        8.98
Today	total        1.13

So I've been logged in to tty7 (graphical desktop) for 43 minutes, but ac shows 1.13

That's because I've also had a terminal open for about 23 minutes.

Sorry, but I don't know how to filter this out.

---

### Post by Royal_Pwner on 2007-12-09
Could anyone else help? Please?
Darn it.
Would it work if I didn't open a terminal? no?

---

### Post by norfair on 2007-12-09
> **Royal_Pwner said:**
> I just got an ubuntu computer.

Hello. I'm not equipped to answer your question, but I hope you won't mind me asking you one... I'm looking to buy a computer with Ubuntu pre-installed and thought I found one with Dell's Inspiron 530N, but I just finished a chat session with them and it seems it's not EnergyStar compliant. So now I am on the hunt for another desktop with Ubuntu. So, if you don't mind me asking, where did you get yours? Thanks.

---

### Post by jflaker on 2007-12-09
in Synaptic there is a package call "sac"  it does all that too........maybe worth a look.

---

### Post by Royal_Pwner on 2007-12-09
I would say look at the system76 computers. I'm using that now, and they're absolutely amazing.

And the sac thing has the same problems, I think. UGH.

---

### Post by norfair on 2007-12-09
> **Royal_Pwner said:**
> I would say look at the system76 computers. I'm using that now, and they're absolutely amazing.

Thanks for the reply. I looked at those, but they are more than I want to pay. I really to like that Koala mini though...

---

### Post by Royal_Pwner on 2007-12-09
Yeah. You could build your own, if you're ambitious, too. Well, I'm not exactly an expert, but I'd say system76 is worth it. Good luck on finding what you need.

---

### Post by jordanmthomas on 2007-12-09
Well, I was trying to this in one line but it got a little long and I was being inefficient.
```
last | grep $USER | awk '{print $9}' | grep "(" | sed 's/(//g' | sed 's/)//g'

```
This will give you a list of times.  This is how long you stayed on for each session.  This list does not take into account times that the computer crashed though.
This list could be put in to something that can add them.  I have finals tomorrow so I don't have time to write something that can add times (but it really isn't difficult...I just really need to be studying ;) )

---

### Post by Krydahl on 2007-12-10
OK, what jordanmthomas has posted doesn't quite work for me, but it's close.

What is it precisely that you're after? When I type last, it gives me the times I was on each terminal session and also the log on times to X (the windowing system). 

So I get:
```
al       pts/0        :0.0             Mon Dec 10 11:05   still logged in   
al       pts/0        :0.0             Mon Dec 10 11:00 - 11:01  (00:00)    
al       pts/0        :0.0             Mon Dec 10 10:59 - 11:00  (00:00)    
al       pts/0        :0.0             Mon Dec 10 10:53 - 10:56  (00:03)    
al       tty7         :0               Mon Dec 10 10:38   still logged in   
reboot   system boot  2.6.22-14-generi Mon Dec 10 10:38 - 11:05  (00:26)    
al       pts/0        :0.0             Sun Dec  9 23:07 - 23:07  (00:00)    
al       pts/0        :0.0             Sun Dec  9 22:25 - 22:26  (00:00)    
al       pts/0        :0.0             Sun Dec  9 21:22 - 21:24  (00:02)    
al       pts/0        :0.0             Sun Dec  9 21:06 - 21:06  (00:00)    
al       pts/0        :0.0             Sun Dec  9 18:40 - 18:40  (00:00)    
al       pts/0        :0.0             Sun Dec  9 18:39 - 18:40  (00:00)    
al       pts/0        :0.0             Sun Dec  9 18:23 - 18:23  (00:00)    
al       pts/0        :0.0             Sun Dec  9 18:22 - 18:22  (00:00)    
al       pts/0        :0.0             Sun Dec  9 18:18 - 18:19  (00:01)    
al       pts/0        :0.0             Sun Dec  9 13:54 - 13:56  (00:01)    
al       pts/0        :0.0             Sun Dec  9 13:38 - 13:38  (00:00)    
al       pts/2        :0.0             Sun Dec  9 11:48 - 13:37  (01:48)    
al       pts/1        :0.0             Sun Dec  9 11:40 - 13:37  (01:57)    
al       pts/1        :0.0             Sun Dec  9 11:17 - 11:28  (00:11)    
al       pts/0        :0.0             Sun Dec  9 11:11 - 12:04  (00:53)    
al       tty7         :0               Sun Dec  9 10:27 - 23:11  (12:43) 
``` 

The time on X are the lines with tty7 in them. The final column appears to give the duration of each session.

Now it seems to me that the difficulty here is most of the work you're doing (I'm guessing) will be using apps (OpenOffice, whatever) not a terminal, so the lines with pts in them aren't much use to you. If the time that the computer was on will do, then we can get that from the tty7 lines fairly easily. If you want the time you were actually working then I'm not sure how you'd do it. Unless you want to go with the fairly basic option of opening a terminal window when you work and closing it when you stop. Even then you'd have problems, because you'd have to make sure you never opened a terminal window at any other time or that would get included in the count.

Anyway, if you can live with the time you've had the machine on, I can write you a script to add that up (though I'm no scripting expert and I don't promise it will be the most efficient way of doing it). If you need actually time working I don't know what to suggest - perhaps one of the many stopwatch utilities out there? You could just start it running when you start working and stop it when you finish.

---

### Post by benson444 on 2007-12-10
> **jflaker said:**
> in Synaptic there is a package call "sac"  it does all that too........maybe worth a look.

I think that's what you want, Royal. It's a newer version of ac and has an option to show usage for each tty. Read the manual page

man sac

This will give you your usage for yesterday:

sac -t -s 12/09/07 -e 12/09/07

-t means split into each tty, -s is start date and -e is end date. I've checked the output against that of 'last' and it all looks right to me.

---

### Post by Royal_Pwner on 2007-12-10
That command works like a dream. Thank you.

---

