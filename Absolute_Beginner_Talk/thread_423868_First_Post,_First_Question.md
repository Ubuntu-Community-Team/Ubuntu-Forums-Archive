---
title: "First Post, First Question"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by HurricaneDan on 2007-04-26
Having just recently set up Feisty Fawn server I feel pretty good about what I have accomplished.  I let it install the LAMP set up, then I configured a static ip address,  I set up webmin and it actually worked!

And let me just say that although I am having issues with the following ssh issue I am really enjoying my first ubuntu (and Linux) experience.

Where I am having issues is with using an ssh connection from my Mac.  When I try to connect it attempts to connect as my username on the Mac.  I want to connect as my user account on the ubuntu server.  I found this online and will test it tonight: 'ssh -l yourusername servername'.  I am not sure what the -l does though.

Now for my question, when I am connected through ssh as my Mac user (which I ended up granting sudo rights) and I try to create an index.html page and a phptest.php page I get a permission denied error when I try to save in either vi or nano.  If I use the following: 'sudo nano /var/www/index.html' nano never loads.  Does anyone know of a solution for this or maybe how to grant other users write rights to the /var/www folder?

Thanks,

Dan

---

### Post by Cypher on 2007-04-26
The "-l" option to ssh indicates "login name". By default, if you issue "ssh <server>" your username on the client machine is used. You can easily change that by doing "ssh user@server" and it will prompt you properly.

You can, of course, alleviate this issue by creating the same user name on both your Ubuntu and MAC machine.

As far as /var/www goes, rather than putting your files there. Create a "public_html" directory in your local home directory, you will have all the right access there. Then when you access your webserver (Ubuntu), you'd do "http://server/~username" and it will pull the files from the "public_html" directory..

---

### Post by HurricaneDan on 2007-04-26
> **Cypher said:**
> As far as /var/www goes, rather than putting your files there. Create a "public_html" directory in your local home directory, you will have all the right access there. Then when you access your webserver (Ubuntu), you'd do "http://server/~username" and it will pull the files from the "public_html" directory..

Thanks for this info.  I really appreciate the help with the ssh. 

Do I need to make a change to etc/apache2/apache2.conf to pull from this folder or is this pre-configured somewhere?

Also, my intention is to set up two websites that are hosted on this machine.  If I create "public_html/site1" and "public_html/site2" can I configure apache to serve these as site1.com and site2.com?

Thanks again,

Dan

---

### Post by Cypher on 2007-04-26
The option of using "public_html" is called User Directories and it was an option that was enabled by default for a long while, but I think in more recent editions of Apache, this feature has been turned off.

Edit the file "/etc/apache2/apache2.conf" and search for 'public' and you will see what I mean, if there is a # in front of the whole block, then remove it, restart Apache and you should be OK.

If you just do "server" then it will default to /var/www (which is configurable in the apache2.conf, BTW) and if you append the "~username", it will go to the user's public_html directory, what you're trying to do here is either create virtual domains or subdomains within a given domain.

Unfortunately, I have done neither of those as I've only used the "~username" method to do tests on my website and then use my webhost to manage the rest.

However,you will get all sorts of good information from Apache's website in regards to [Virtual Hosts]("http://httpd.apache.org/docs/2.2/vhosts/").

Good luck..

---

### Post by Cypher on 2007-04-26
[deleted]

---

### Post by az on 2007-04-26
> **HurricaneDan said:**
>   If I use the following: 'sudo nano /var/www/index.html' nano never loads.  Does anyone know of a solution for this or maybe how to grant other users write rights to the /var/www folder?


You can log into your box using

ssh [email]you@example.com[/email]

There should be no reason that you cannot write to /var/www using sudo, unless your user does not have sudo priviledges.

It is not a good idea to chown or add write privs to /var/www to the web server user (www-data).  It's a good idea to make it diificult for any process running through apache to have write access to your drive.  Especially if you are running a database-driven site using php.

To allow your box to host several site, just create the site in /etc/apache/sites-available

Copy the default and give it a different name.  Edit the document root and the ServerName and you are good to go.  You can run as many sites as you want from that box.

Enable/dissable a site using a2ensite/a2dissite

sudo a2ensite forum
sudo a2dissite default


Restart apache to make changes take effect

sudo /etc/init.s/apache2 restart

---

