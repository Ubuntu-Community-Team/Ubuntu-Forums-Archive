---
title: "Which is the correct way to install &quot;mysql&quot; - when you are given 2 install methods?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-01-24
Hello!

I found two ways to install "**mysql**", but I am not sure which is the best...

Is it this one:

**a**. [color=blue]apt-get install mysql-server-5.0[/color] [color=green]--prefix=/usr/local/mysql[/color]

OR, this one (shorter version):

**b**. [color=blue]apt-get install mysql-server-5.0[/color]

_Questions_:

1. What does the former method do compared to the later?
2. Are there any advantages on using the above install method "**a**" compared to install method "**b**"?
3. Why when using the option [color=green]--prefix=/usr/local/mysql[/color], I get the following error:
[color=red]E: Command line option --prefix=/usr/local/mysql is not understood[/color]
Has the "[color=green]--prefix[/color]" notation been dropped or replaced with some other one?

Thanks.

P.S.> In the above install method "**a**", I was then suggested to install "apache2" & "php5" in the following way:

	1. apt-get install apache2 --prefix=/usr/local/apache2 --enable-module=so

	2. apt-get install php5 --prefix=/usr/local/php --with-mysql=/usr/local/mysql \
				--with-apxs2=/usr/local/apache2/bin/apxs

---

### Post by daemonoid on 2007-01-24
I think the first version is an attempt at installing mysql in the directory specified. Thing is, as you found out, it probably wont work - the --prefix is often used to relocate rpms but i've never seen it used with apt-get.

I'd suggest using synaptic (ubuntu's gui installer) just select mysql, php and apache, hit apply changes and all should go well...

But if you really want to use apt-get then just use the b option.

---

### Post by dvarsam on 2007-01-24
[QUOTE=daemonoid]I think the first version is an attempt at installing mysql in the directory specified. Thing is, as you found out, it probably wont work - the --prefix is often used to relocate rpms but i've never seen it used with apt-get.
I'd suggest using synaptic (ubuntu's gui installer) just select mysql, php and apache, hit apply changes and all should go well...
But if you really want to use apt-get then just use the b option.[/QUOTE]

S, basically it is impossible in Ubuntu to install an application on a user specified path?
I.e. IF it is possible, how can it be done?

---

### Post by daemonoid on 2007-01-29
I'm not 100% sure, but if you really don't like the ubuntu defaults try downloading the deb and use the --prefix command.

AFAIK apt-get has the same restrictions on all linux versions. Synaptec and aptitude are the same. Then again, nowadays so is windows - all the larger software will only install to program files.

Further to that, a quick search for how to install mysql in a different path (using rpms) seems to uncover a lot of troubled users.

Is there any particular reason you need it in another dir? maybe if you explain the full problem then i or someone else can try to sort that out...

---

### Post by dvarsam on 2007-01-29
[QUOTE=daemonoid]I am not 100% sure, but if you really don't like the ubuntu defaults try downloading the deb and use the --prefix command.[/quote]

In what way will this be different?
I mean, I am not installing it...
So, what is the gain involved IF I download it to a specific folder?
The problem is with _installing_ on a specific folder, NOT downloading on a specific folder...


[quote=daemonoid]Further to that, a quick search for how to install mysql in a different path (using rpms) seems to uncover a lot of troubled users.[/quote]

What do you mean?
Can you please explain?

[quote=daemonoid]Is there any particular reason you need it in another dir? maybe if you explain the full problem then i or someone else can try to sort that out...[/QUOTE]

From what I remember, in Ubuntu v6.06 you were given the choice to install to a specific folder...
Now, in Ubuntu v6.10, IF I try to use the "--prefix=..." option, I get the following error:

[color=red]Error: option "--prefix=..." not understood.[/color]

So, has the option "--prefix" been replaced with some other option?
a newer one (maybe)?

Thanks.

P.S.> There is NO specific reason why I want to do install in specific folder, but the HowTo I had bumped to (back then), was following this install approach...
NOT only for mysql, but for apache & php too!
The HowTo did Not clarify why it was suggesting to install on a user specified folder (instead of the default ones)...
So I can't answer that...
Maybe _you_ can! Was it for security reasons?
I really wonder...

---

### Post by steve.horsley on 2007-01-29
The man page for apt-get does not contain the word prefix anywhere. Where did you get that from? And why are you trying to override the package's chosen directories anyway. Actually, since most packages scatter files all over the place like confetti in a storm, I can't see any practical use for a frefix option.

---

### Post by dvarsam on 2007-01-29
Hey "steve.horsley",
long time to see you dude!
You don't hang out so much nowadays at the Forums, do you? :)
I am happy to see you back! ;)

[QUOTE=steve.horsley]The man page for apt-get does not contain the word prefix anywhere.[/quote]

I know!
I looked for that too!
Is it possible that it dot dumped recently?
i.e. Between v6.06 -> v6.10 or v5.10 -> v6.10?
Or that is something that is never supposed to happen?


[quote=steve.horsley]Where did you get that from?[/quote]

I can't recall where I got that HowTo from...

[quote=steve.horsley]And why are you trying to override the package's chosen directories anyway.[/QUOTE]

I wasn't trying to override anything...
I was just following the HowTo instructions.
I had kept a copy of that HowTo & decided recently to try it out on v6.10.
I thought they were doing this probably for security reasons... (i.e. hacher attempts...)
They were NOT clarifying why...
But that was what their HowTo instructed...

[quote=steve.horsley]Actually, since most packages scatter files all over the place like confetti in a storm, I can't see any practical use for a frefix option.[/QUOTE]

Could it be for security reasons?

Anyway, a couple of days ago, I quit the process of using that "--prefix" option & installed everything as the Ubuntu Papa/Wiki was suggesting...
I couldn't find a workaround on this, so I dumped performing a custom install...

Thanks.

---

### Post by steve.horsley on 2007-01-30
Hi there dvarsam. I'm still around quite regularly. But I do seem a little busier these days, and with the forums having more than doubled their user base recently, my output is even more diluted. Others often beat me to giving an answer, but that is a Good Thing.

I really can't imagine what --prefix does, unless it substitutes a different filesystem root, as in when an installer is installing to a hard drive working from a RAM filesystem. Googling just found me one reference to using --prefix with rpm but saying that didn't work with apt-get.

Glad you got it going anyway.

---

### Post by daemonoid on 2007-01-30
I didn't mean just download to a different directory, i meant download the .deb file for mysql and then install using the --prefix option.

The troubled users - basically all manner of errors when i did a google search for something along the lines of mysql change path

As for apt-get and --prefix (i'm going out on a limb here) i'm 99% sure that it never allowed the use of the --prefix option. Also a quick man and google search shows no such options, basically apt-get holds your hand through this and there are some options that are just not possible. If you want to relocate mysql you'll have to get 'hardcore' and do it from the .deb or source code.

I'm guessing it was a non-ubuntu howto? 
Creating a mysql user and moving the installation to /usr/local/mysql is a good security measure rather than using root for obvious reasons.
I believe both apt-get and synaptec both do all of this automatically.

---

### Post by dvarsam on 2007-01-30
[QUOTE=daemonoid]I didn't mean just download to a different directory, i meant download the .deb file for mysql and then install using the --prefix option.[/quote]

I have not done it by the above method you mentioned...
I guess I will have to try this at some point...

[quote=daemonoid]
As for apt-get and --prefix (i'm going out on a limb here) i'm 99% sure that it never allowed the use of the --prefix option. Also a quick man and google search shows no such options, basically apt-get holds your hand through this and there are some options that are just not possible. If you want to relocate mysql you'll have to get 'hardcore' and do it from the .deb or source code.[/quote]

ok, thanks man.
I don't want to mess up the source code...
I try to keep things as easy as possible.
I guess I was wrong thinking that this was possible in older versions of Ubuntu...

[quote=daemonoid]I'm guessing it was a non-ubuntu howto? 
Creating a mysql user and moving the installation to /usr/local/mysql is a good security measure rather than using root for obvious reasons.
I believe both apt-get and synaptec both do all of this automatically.[/QUOTE]

I don't know where this HowTo was originating from...
Sorry!
I guess that apt-get & Synaptic have a pre-defined directory where everything get installed & I don't think it would be easy to tamper the destination directories from the source files.

I want to thank you all for sparing some of your time to clear this out...
Thanks again,

dvarsam

---

