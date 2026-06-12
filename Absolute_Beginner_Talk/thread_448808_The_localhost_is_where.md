---
title: "The localhost is where?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by PhilKE3FL on 2007-05-19
I'd like to know:

Where is the localhost? 

Can I write Perl scripts on it?

Where would I put them?

How would I run them?

Thanks,
Phil K

---

### Post by zekopeko on 2007-05-19
localhost is your computer.

---

### Post by PhilKE3FL on 2007-05-25
Does this mean I can write Perl scripts & run them?

Can I run them from the local host via a browser?

Can I run them from the command window?

If so, how do I do that? I've tried running Perl scripts in a browser but on my Windows PC I would run them by first going to the localhost: [http://localhost/JS/index.html](http://localhost/JS/index.html)

But I know where the "localhost" is on that PC & so I  was able to make a JS directory & my Perl scripts will run.

When I did that with Linux it did not work, why? Again, where do I put Perl scripts so they will run in a browser, where dio I put them to run them from the command window? Probably right there?

---

### Post by pmg on 2007-05-25
Using "localhost" is a way to address the loopback interface, to talk to the computer you're  on as if going over the network.  To use an address [http://localhost/](http://localhost/)... you would need to be running a web server on that machine.  The apache web server, the most widly used web server in the world, will run on ubuntu.  Part of the web server config tells it how to map names, and where the top level of it's tree is.

But, before going to all the work of installing and setting up apache, if you don't really need all the power of a web server and you just want to view files on your own machine, you can refrence them with a file URL.  For example to reference the file /home/JS/index.html in firefox you can use file:///home/JS/index.html  (note that there are three /'s after "file".

---

### Post by PhilKE3FL on 2007-05-28
Thanks pmg I got that working but I guess I will have to go to Apache because I really would like to have the ability to run Perl scripts from a server so when the Internet is down I can still develope code.

My Windows laptop runs Apache but only with PHP, I guess I should also figure out how to get Perl on it as well.

---

