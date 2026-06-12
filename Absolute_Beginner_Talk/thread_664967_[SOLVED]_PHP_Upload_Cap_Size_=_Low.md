---
title: "[SOLVED] PHP Upload Cap Size = Low?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-01-11
Hey, I have some no-name PHP upload script (HTML form to a PHP upload script) and it's capping the file size really low (like 1mb) - A friend of mine said there's a PHP size limit in the config file - but I couldn't find anything resembling it or that would limit it to that.

Anybody know what file limitations would exist?

PS:  I don't have a "MAX FILE SIZE" option in the HTML form.

---

### Post by Miademora on 2008-01-11
Most likely this one

; Maximum allowed size for uploaded files.
upload_max_filesize = 2M

or

post_max_size = 8M

---

### Post by Syndacate on 2008-01-11
> **Miademora said:**
> Most likely this one

; Maximum allowed size for uploaded files.
upload_max_filesize = 2M

or

post_max_size = 8M

I changed them both to 10M and I tried uploading a 4.4MB file and it failed.

Any other suggestions?

---

### Post by Miademora on 2008-01-12
Did you restart Apache? Did you modify the correct php.ini?

please check if the changes have been applied like

```
echo ini_get('post_max_size');
echo ini_get('upload_max_filesize');

```

You could check if theres a memory_limit set in php.ini wich might not be big enough. Or try to increase errorlogging level.

Check if the file gets uploaded with something like this:

```
print_r($_FILES['nameofyourpostfield']);
exit;
```

Next you could check apache for [http://httpd.apache.org/docs/2.0/mod/core.html#limitrequestbody](http://httpd.apache.org/docs/2.0/mod/core.html#limitrequestbody)

Or search in the php.ini for values with 1M wich sound like they might conflict and raise them.

P.S. code untested

---

### Post by Syndacate on 2008-01-12
> **Miademora said:**
> Did you restart Apache? Did you modify the correct php.ini?

please check if the changes have been applied like

```
echo ini_get('post_max_size');
echo ini_get('upload_max_filesize');

```

You could check if theres a memory_limit set in php.ini wich might not be big enough. Or try to increase errorlogging level.

Check if the file gets uploaded with something like this:

```
print_r($_FILES['nameofyourpostfield']);
exit;
```

Next you could check apache for [http://httpd.apache.org/docs/2.0/mod/core.html#limitrequestbody](http://httpd.apache.org/docs/2.0/mod/core.html#limitrequestbody)

Or search in the php.ini for values with 1M wich sound like they might conflict and raise them.

P.S. code untested

Wow, I feel like a complete retard - I read your post (as there's only one php.ini file I know of) and restarted apache and it worked fine with a 4.8mb file, and then again with another 4.4mb file :-\.

Oh well - working now, I guess.

Just for future reference, what should the memory usage that PHP should be allowed to use, be?  This isn't a "server computer" (not dedicated) and 99.9% of the time there won't be more than one person using one BASIC PHP form - but in terms of size for the upload script - how much memory should I let it have?

PS:  When I restarted apache it gave me some bull about it not being able to find my my IP address (so it assigns 127.0.1.1) - any way to tell it what my IP is?  Since sendmail is having the same problem and causing +60 seconds on boot - and this I saw in the apache logs, plus it showed up on konsole when I restarted apache.

---

### Post by Miademora on 2008-01-12
Well since its working you dont need to change more things id say.

You wont need memory_limit for the upload itself. But if the file gets loaded afterwards for further processing you need to make sure you have enough memory. Depending on the script i usually set it to twice the filesize+3MB or if the script supports only loading chunks of the file then i use twice the chunksize +3MB. When you expect only a few users and have a max. filesize of 10MB i think it would be safe to go with 23MB+ or something.  It all depends on what you do with the filecontent afterwards.

About the ip-issue im not sure whats the problem. Id suggest to open a new thread with the exact errormessage unless someone jumps in and has a solution in the next hours.

---

### Post by Syndacate on 2008-01-12
> **Miademora said:**
> Well since its working you dont need to change more things id say.

You wont need memory_limit for the upload itself. But if the file gets loaded afterwards for further processing you need to make sure you have enough memory. Depending on the script i usually set it to twice the filesize+3MB or if the script supports only loading chunks of the file then i use twice the chunksize +3MB. When you expect only a few users and have a max. filesize of 10MB i think it would be safe to go with 23MB+ or something.  It all depends on what you do with the filecontent afterwards.

About the ip-issue im not sure whats the problem. Id suggest to open a new thread with the exact errormessage unless someone jumps in and has a solution in the next hours.

I don't do anything with the file - it drops it in a folder (it's just an upload script).

So what should it be for that - no action - just puts it there.

---

### Post by Miademora on 2008-01-12
Then your settings are fine regarding the fileupload. Time to focus on your other problems :)

---

### Post by Syndacate on 2008-01-14
> **Miademora said:**
> Then your settings are fine regarding the fileupload. Time to focus on your other problems :)

Yeah, I don't know, my friend said it's just some dick on campus running bots at random IP's.

---

### Post by Syndacate on 2008-01-16
Ah damn, I thought the problem was gone, but it's not.

I changed them both to 10M the first time, then it worked with a 4.4mb file.

I changed it to 50M (both the post_max_size and upload_max_size) and tried uploading a 14mb file and it failed :(.

Anything else around that can limit the upload size?

I never intend to, but I wanna have it so if I need  to upload a 700mb image I can do so just by changing a few settings to extend the max sizes.

---

### Post by Syndacate on 2008-01-17
Blah, nvm, it's because I didn't restart apache - I restarted my computer and it worked and I was wondering why - and then it finally hit me that apache was restart when my computer was.

haha @ me.

---

