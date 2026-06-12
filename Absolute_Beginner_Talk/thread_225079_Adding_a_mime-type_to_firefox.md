---
title: "Adding a mime-type to firefox"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by OU812 on 2006-07-29
Hello. I'm trying to install the emusic download manager. It says I have to tell firefox how to launch the dlm:

> To launch the eMusic Download Manager when you click on an eMusic download link, follow the instructions below. Please note that due to the great number of web browsers that are available for Linux, we cannot provide detailed instructions for each of the browsers out there. The following instructions are general instructions that should apply to most web browsers on Linux:

   1. Open the preferences dialog in your browser.
   2. Look for a section in the preferences called 'Helper Applications', 'Handlers', or 'MIME-types'.
   3. Add a new mime-type/helper application/handler for the eMusic Download Manager. For this step you will need to know the following pieces of information:

      A. Extension: .emp
      B. MIME-Type: application/vnd.emusic-emusic_package
      C. Helper application: emusicdlm

You should also turn off any 'Ask me before opening downloaded files of this type' options, and ensure that the browser does not save the file to disk instead of opening the emusicdlm application. 

But I can't find anything from part 2. Any ideas? Thank you.

john

EDIT
I think I got past this - I just went to emusic.com and downloaded a song. When firefox asked me which app to use, I navigated to /usr/bin/emusicdlm. It launched. But it gave me a cannot connect error. The help file said

> Q. What do I do if I am using the eMusic Linux Download Manager 2.0 and receiving "Cannot Connect" errors.

A. The GNU libc libraries which are distributed with the eMusic Download Manager 2.0 make use of a daemon which must be installed and running in order to use the eMusic Download Manager 2.0 effectively. If you do not have this installed and running, you may receive a "Cannot Connect" error message. This daemon, known as the Name Service Caching Daemon (NSCD) is used to handle DNS queries. In order to avoid any "Cannot Connect" error messages, we suggest that you have a running NSCD on the same machine that you are running the eMusic Download Manager 2.0 on.


How do I deal with the nscd issue? Thanks.

---

### Post by OU812 on 2006-07-29
I checked the prefs in the dlm app. There is an option for typing in the command to launch your web browser. So I entered "firefox". When I tested it (I cliced on the link to the emusic homepage), it gave me this error: "Could not find the specified brower. Please check your browser settings." How could this be? If I type "firefox" in a terminal, it launches. So how come it doesn't work within the app? Any ideas, please? Thanks.

john

---

### Post by atrus123 on 2006-09-02
Did you ever figure this out?  I have had similar problems, and [this link](http://bradyjoslin.com/onlinux/?p=4) helped me out.

Here's the crucial stuff:
```

1. I install the “tinyproxy” package:
# apt-get install tinyproxy

2. I edited /etc/tinyproxy/tinyproxy.conf, adding the line
Listen 127.0.0.1

3. Run /etc/init.d/tinyproxy restart

4. In the Emusic DLM under Network Preferences, I put 127.0.0.1 as the http proxy, and 8888 as the port number (or whatever tinyproxy is running on) 
```

---

### Post by gb5757870 on 2008-03-19
Very appreciated. I can confirm that this works just after having just downloaded emusic

---

### Post by davygravy on 2008-03-19
also confirming this works!

way to go!

perhaps emusic should consider coding around this problem?  or making tinyproxy a dependency?

---

