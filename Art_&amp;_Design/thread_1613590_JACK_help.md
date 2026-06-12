---
title: "JACK help"
date: 2010-11-04
forum: Art &amp; Design
---

### Post by icedice on 2010-11-04
i dont really know were to post this but music is an art so i gues ill post here..

i recently got ardour to do some recoding in but im having a problem with JACK. heres the message i get

```

 p, li { white-space: pre-wrap; } [COLOR=#999999]17:00:09.458 Startup script...[/COLOR]
 [COLOR=#990099]17:00:09.459 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]17:00:09.870 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]17:00:09.872 JACK is starting...[/COLOR]
 [COLOR=#990099]17:00:09.880 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 [COLOR=#999999]17:00:09.972 JACK was started with PID=10232.[/COLOR]
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]17:00:09.999 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]17:00:10.001 Post-shutdown script...[/COLOR]
 [COLOR=#990099]17:00:10.002 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]17:00:10.449 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]17:00:12.021 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
```[COLOR=#ff0000][COLOR=Black]
[/COLOR][/COLOR]
[COLOR=#ff0000][COLOR=Black]idk whats wrong and i really need this to work within the hour. any help?[/COLOR]
[/COLOR]

---

### Post by Sylos on 2010-11-04
Have you tried following the instructions it gives you in the terminal output:

```
Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!

```

Seems like a good place to start.

---

### Post by icedice on 2010-11-04
got it working! thanks for the help!

---

