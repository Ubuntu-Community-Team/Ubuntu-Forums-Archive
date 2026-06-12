---
title: "[SOLVED] problem opening playlists in serpentine"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Shaktipwr on 2007-08-04
I am so absolutely frustrated and I know there is a simple answer.  I am trying to burn a CD using Serpentine but when i try to open a playlist from Rhythmbox it's as if I never issued the command.  I can't copy and paste songs in and when i try to drag and drop I am told the songs are an unsupported file type.  I have at this point installed practically every gstreamer plugin synaptic has. I have been successful burning directly from rhythmbox but those discs won't play in my car stereo so I want to try something different. I also installed gnomebaker but when I try to add songs I get this message "The plugin to handle a file of type application/x-desktop is not installed."  Not really sure what that means. I am feeling very hopeless at this point.
I have searched everywhere for the answer to this question and have tried all sorts of things to make it work.  I am new to linux and am trying to learn so please be very basic with any replies you send.  I am going on a long trip this weekend and want my music from my computer.  Please help.  Thanks!
I am Feisty Fawn Model S62FM

---

### Post by apswartz on 2007-08-04
install k3b and use it. IMHO it is simpley the best CD burner GUI in linux (Shoot, I like it better than anything I've seen on Windows and Mac systems).

Note, if you use mp3s you will need to install the kde mp3 library files.
```

sudo aptitude install k3b libk3b2-mp3

```

---

### Post by Shaktipwr on 2007-08-04
I will try that, thanks.  I am feeling rather defeated though over the whole serpentine issue.  So many people seem to be able to use it, why can't I?

---

### Post by apswartz on 2007-08-04
You can check out the known bugs for Serpentine at....
Ubuntu...
[https://launchpad.net/serpentine](https://launchpad.net/serpentine)
Gnome...
[http://bugzilla.gnome.org/buglist.cgi?product=serpentine&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED](http://bugzilla.gnome.org/buglist.cgi?product=serpentine&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED)

Also, will the cds from rhythmbox play on cd players other than the one in your car?

---

### Post by Shaktipwr on 2007-08-05
The CDs will play in other players.... I am actually replacing my car stereo so that may help.  The ones that play tho don't seem to have all the songs that supposedly burned.  I am encountering other problems with my system as well so am trouble shooting a lot of stuff and trying to clean up a lot of stuff.  Hopefully all this will help in some way.  Thanks for your help.  Checking out those sites on bugs....never thought to do that, now I have that resource too!

---

### Post by apswartz on 2007-08-05
No Problem.

Do you plan to check out k3b?

---

### Post by Shaktipwr on 2007-08-07
I grabbed K3b and am playing with it.  The problem is my machine keeps hanging up and K3b makes it worse.  Once I finish working on my machine I will spend more time......

---

### Post by Shaktipwr on 2007-08-08
WOO HOO!!!  OK, all problems fixed on my machine, everything is nice and clean!  I have succesfully burned a CD with K3b and will never look back for Serpentine.  Thank you all for your attention and help.  Mark this one as solved!

---

