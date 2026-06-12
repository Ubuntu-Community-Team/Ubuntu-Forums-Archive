---
title: "Unable to install Thurnderbird and Firefox extensions"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-09-19
I'm in the process of transitioning from Windows to Ubuntu [on a different machine]. One of the things I want to do is install the extensions I used on Thunderbird and Firefox. I've downloaded the extensions, but Ubuntu won't allow Thunderbird or Firefox access to the program folders in /home/eric where the extensions are stored. There are folders for extensions in the Thunderbird and Firefox folders, but I can't get to them.

How do I install my extensions?

Thanks,

---

### Post by jamvegan on 2007-09-19
The easiest way to install add-ons in Firefox is simply to click Install Now on the add-on's download page.  To install in Thunderbird, these instructions from the mozilla site worked for me:
> How to Install in Thunderbird

   1. Right-click the link below and choose "Save Link As..." to download and save the file to your hard disk.
   2. In Mozilla Thunderbird, open Add-ons from the Tools menu.
   3. Click the Install button, and locate/select the file you downloaded and click "OK".

I'm not sure what you mean about Ubuntu preventing the programs from accessing a directory.  I can access any regular directory that I have created in my home directory via either program.  What are the permissions on the directory in question?  Did you create it in Ubuntu or copy it from somewhere else?

---

### Post by sunexplodes on 2007-09-19
Open a terminal and give this a shot:

sudo chown -hR yourusername /home/yourusername

That makes sure your username has ownership of everything in your home directory, and SHOULD in theory solve that problem. 

Failing that, open firefox and thunderbird with Sudo, install your extensions, then go back to regular use.

---

### Post by Eric Weir on 2007-09-27
> **jamvegan said:**
> The easiest way to install add-ons in Firefox is simply to click Install Now on the add-on's download page.  To install in Thunderbird, these instructions from the mozilla site worked for me:

My apologies for not getting back to you and the other member who responded to me. What you suggested is how I ended up doing it

>  I'm not sure what you mean about Ubuntu preventing the programs from accessing a directory.  I can access any regular directory that I have created in my home directory via either program.  What are the permissions on the directory in question?  Did you create it in Ubuntu or copy it from somewhere else?I was trying two things: [1] save downloaded extensions to the mozilla folder in /etc, which I understand can't be done without changing permissions,  and [2] save downloaded extensions _directly_ to the extension folder in the firefox profile, which you can't do because the folders are hidden. They _can_ be copied to the extensions using Nautilis after they've first been saved to a non-hidden folder, e.g., /eric/desktop.

Thanks for your help.

---

### Post by Eric Weir on 2007-09-27
> **sunexplodes said:**
> Open a terminal and give this a shot:

sudo chown -hR yourusername /home/yourusername

That makes sure your username has ownership of everything in your home directory, and SHOULD in theory solve that problem.

I'm brand new. Haven't tried terminal or sudo, yet, though getting back to the command line was one of the things I was looking forward to in Linux. I was pretty comfortable with it in the pre-Windows MS-DOS days.

>  Failing that, open firefox and thunderbird with Sudo, install your extensions, then go back to regular use.As I explained to jamvegan, I somehow figured out that I could use Nautilis to copy the extensions to the extensions folder in my Firefox profile after  downloading them to a nonhidden file, e.g., /eric/desktop.

Thanks for the suggestions, and I will get to the terminal.

---

