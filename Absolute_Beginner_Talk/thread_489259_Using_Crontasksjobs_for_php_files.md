---
title: "Using Crontasks/jobs for php files"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by JuicedJuice on 2007-07-01
Hi, I'm new to Linux and I can only seem to find overly technical details on how to set up cron tasks  to execute tasks at specified periodic times. If I have a web server going and I want to run a php file every 5 minutes that is in my base web folder or some folder within (var/www/somefolder) what do I need to exactly do step by step assuming I know nothing about cron? I can't emphasize the step by step part enough. I just need a good example to get me going. Thanks much for help.

---

### Post by Raineer on 2007-07-01
Run the following

**sudo crontab -e**

This will open nano into a temp file, which after you update and write your changes will update the cron table for you.  The **-l** flag will let you see what's currently scheduled.

Assuming the cron daemon is setup properly, you can enter events and when you want them to be processed. 
"man crontab" will help you out a ton but I'll get you started

30 16 * * * /home/me/scripts/fourthirty.sh

Is the entry that will run script "fourthirty.sh" at 4:30 PM every day.  However, I do not know the syntax for running something "every 5 minutes".  That might be a job for **anacron**. I don't use scripts on that short of intervals, but cron/crontab works perfectly the way I listed above.

The 3 asterisks stand for day of the month, month, and day of the week.  Worst-case you could setup entries for each time you wish to run but I have a feeling there's an easier way to do that.

---

### Post by apjone on 2007-07-01
What exactly do you want to do, a php file is a web page and mainly only executes when you browse to it. You would probably be best with a bash script. 

If i knew waht you wanted to do I could guide you better.

*/5 i believe is every 5 mins

---

### Post by JuicedJuice on 2007-07-01
> **apjone said:**
> What exactly do you want to do, a php file is a web page and mainly only executes when you browse to it. You would probably be best with a bash script. 

If i knew waht you wanted to do I could guide you better.

*/5 i believe is every 5 mins

I want to execute the code in the php script on a set timer basically.

---

### Post by apjone on 2007-07-01
What does the code do?

---

### Post by JuicedJuice on 2007-07-01
> **apjone said:**
> What does the code do?

It's not a page that would be used for viewing anything via a browser. For example one of the php pages may load a web page on the internet, get information from that web page and then send that info to a database.

---

### Post by apjone on 2007-07-01
hmm would a bash script not be better than php script?

you could try

```

sudo crontab -l

*/5 *  * * *  /path/to/my/phpfile.php > /dev/null

```

But i have no idea what you would use to invoke a php script. As you will probabaly get permission denied or command not found if you try and run it lke this

---

### Post by JuicedJuice on 2007-07-01
Ok, thanks guys

---

