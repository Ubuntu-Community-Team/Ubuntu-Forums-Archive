---
title: "Just a vent, hanging in there!"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by faedrake on 2007-04-02
I'm looking to vent more than anything.  But, if you have any amazing insights I'm listening.  :)  

Here is a narrative of my adventures of the day.  Now everyone knows what a total newbie I am!

At work I use a Windows Server maintained by our IT department.  I have to ask for anything that needs installing or configuring.  I decided it would be much nicer if I could work on my dynamic PHP-driven PDFs from home.

I have Apache2 and PHP5 running here at home, I could install the PDFlib free version. It should be no problem, right???

First, I have to reboot the PC twice, as usual. It only loads the desktop on the 3rd boot  **like clockwork**.  Other times I get X-Server errors. I still don't know why but I suspect hardware, though nothing is going awry EXCEPT the boot issues. I have spent more hours struggling with this than I will admit here.  I have tried everything referenced in any forums or Google search.

Next, I loaded Firefox (no internet trouble, yay!) and downloaded the PDFlib package for my server type.

Firefox asked me if I'd like to open the file in the archive manager. Sure! Of course, it didn't open with enough permissions for me to actually extract the darn thing. >:(

After some searching and grumbling I finally figure out the command for launching the unzipper with full permissions: sudo file-roller (yes, I am still attached to my gui crutches)

At last, I am able to extract the files! Now what?

The PDFlib installation document is vague (of course). It assumes you already know how to run a Linux server, including php and apache configuration. I find some instructions I think I understand, then I find the PHP binding file .so and copy it to the appropriate directory. Then I change a line in a text file that is supposed to point to the directory, and another line that loads the file.

Now I have to figure out how to restart the Apache server. I finally find some instructions. ./apache2ctl -k stop then -k restart Of course, I have to find the right directory to run the command in. I also had to figure out that I needed to add the number 2 for Apache2

Now, I run my php file with some PDFlib code in it. No dice, the PDFlib class was not found. I try various configurations of directories (and get very good at restarting the Apache server). But, no dice. I pull up my phpinfo() but there is no PDF module to be seen.

So, I read further in the instructions... Maybe other parts have to be installed as well?

It says I can install from the C language bindings. So, I make (install) the C version. Then it says I need to run pear on the PECL download of the pdflib wrapper. Um, yeah, okay.

I find and download the PECL PDFlib. I try to run pear, but I have no pear! :( So, I find and install pear in the package manager.

Now I try running pear again, but it can't find the *phpize* command. Bleh!!! After some searching I realize I need the dev package for php5. I found it and set it to install (along with 9 other packages that it depends on).

I am giving it a rest for now.  This is supposed to be spring break after all.  I'll be back though.  The Windows Vista commercials always drive me back...

---

### Post by amohanty on 2007-04-03
1. Any reason not to use the php in repos and php-fpdf :)
2. To restart any servers installed via synaptic look in /etc/init.d for apache2 it is: 
/etc/init.d/apache2 restart
3. You should not need to do an sudo to decompress a file you downloaded via ff. Probably a permissions problem. ls -al in your home folder would help.

Finally, ever tried installing PHP5 with extensions on windows? :)

Hang in there, though. Trust me, in the long run, php on ubuntu will be save you a lot of pain, tears not to mention hair. 

AM

---

### Post by faedrake on 2007-04-03
1. I'm using PDFlib (have the registered version at work) so we can use our huge library of existing PDFs as templates, and fill them in with dynamic data.  It's nice being able to copy and paste the PDFlib blocks from page to page, then they are set for PHP.  I try not to make them from scratch if I can help it.

2,3 Thanks for the tips.  :)

I'm sure PHP on Windows is no fun.  At least that part isn't my job!

---

### Post by jcolo on 2008-01-02
bumping....

The actual package name is php5-dev  if you want to install something as PDO from PECL... for those of you that get the phpize error message.

I wish an extension like PDO was not an optional package.

Cheers.


JCG

---

