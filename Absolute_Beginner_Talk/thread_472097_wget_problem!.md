---
title: "wget problem!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-06-12
Sometimes when I wget something instead of getting the file, I get an index.html file.

I think this has something to do with the website making sure people aren't just linking to there files.

How do I get around this?

Thanks.

---

### Post by tito13kfm on 2007-06-13
I'm sure there must be a way of altering your referrer through the terminal, but the way I get around this is to just go to the address of the file you are trying to get with wget and download it with firefox to my home folder then I just move it to where I need it with sudo mv

---

### Post by guysmiley25 on 2007-06-13
I understand that is a solution, but sometimes it is not appropriate.

Thanks

---

### Post by bbarcelo on 2007-06-13
If you can use your browser to confirm the link from within the index.html file or view some source and find the direct link to the file, maybe you can try wgetting that instead of whatever link you are currently using. It may or may not work. Any reason you have to use wget to get these difficult files?

---

### Post by guysmiley25 on 2007-06-14
Some times I'm on my server that does not have a GUI, it would save me a step over to one of the client computers.

Any other CLI utility that might do as I require

Thanks

---

### Post by Seisen on 2007-06-14
You can try using lynx its a text-based web browser, that you you can check to see if maybe the link changed.

---

### Post by guysmiley25 on 2007-06-14
There are cases where the file is there however you can only "link" to it from that website.

For example there is a file program.tar.gz hosted on website.com.

The file is located at [http://www.website.com/stuffnthat/program.tar.gz](http://www.website.com/stuffnthat/program.tar.gz)

There is a link to program.tar.gz on [http://www.website.com/index.htm](http://www.website.com/index.htm)

For any other website that links to [http://www.website.com/stuffnthat/program.tar.gz](http://www.website.com/stuffnthat/program.tar.gz). When you click that link you end up at [http://www.website.com/index.htm](http://www.website.com/index.htm).

When I used to mess around with web pages I remember doing something like this, this was to prevent people linking to your downloads without recognition for your website. For example you might have banners that pay for you bandwidth.

What I think is happening is that when you wget [http://www.website.com/stuffnthat/program.tat.gz](http://www.website.com/stuffnthat/program.tat.gz). You are treated as a some other "website".

Sometimes I wish to automate or download these files via the command line. For example I might be at work, but want to ssh into my server, and download from there. Or setup a time when it will be downloaded. Like at the start or the month when I'm on a new billing period.

Thanks

---

