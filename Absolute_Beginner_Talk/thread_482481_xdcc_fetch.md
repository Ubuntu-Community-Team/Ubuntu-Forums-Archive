---
title: "xdcc fetch"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by illmatic on 2007-06-23
hey guys,

i tried to install xdcc fetch ( [http://xdccfetch.sourceforge.net/](http://xdccfetch.sourceforge.net/) ), unfortunatly i need to install ruby what i did via synaptic.
I also read that i need to install fxruby (gui) but i really dont know how (already searched for it on google).
Is there an alternative to xdcc fetch for linux?

so long ill

---

### Post by illmatic on 2007-06-24
could someone pls help i realy nead help!!

---

### Post by illmatic on 2007-06-24
cmon can someon pls help me i really nead this programm !!!

---

### Post by illmatic on 2007-06-30
pls someone help!!

---

### Post by ruza on 2007-06-30
Synaptic? I guess that you should search ruby GUI in synaptic...

---

### Post by illmatic on 2007-07-01
well i coulndnt find anything with synaptic
the only thing i found was "ruby bindings for the Qt4 GUI library" but that didnt help at all:(

---

### Post by shirilover on 2007-07-01
You will to do a few things to get this running. Though, I'm not sure why you need a xdcc catcher/bottler.
First you should probably install rubygems (needs universe repository enabled)
```

sudo apt-get install rubygems

```
Then you will need to install the fox-toolkit, in universe(choose between 1.2, 1.4, and 1.6)
```

sudo apt-get install libfox-1.x-dev

```
Then install FxRuby, this will take a while, lots of warnings
```

sudo gem install fxruby

```
and finally
```

sudo gem install xdcc-fetch

```

---

### Post by illmatic on 2007-07-01
now i got a final question!
not everything worked but the xdcc fetch installation worked
(sudo apt-get install libfox-1.x-dev -> error couldnt find and i installed fxruby version ms32 cause the other version doesnt install correctly)
if i now try to open the "XDCC-Fetch.rbw" file it asks me to start it via console or normally but none of this works...

---

### Post by shirilover on 2007-07-01
Did you substitue a number ( either 2, 4 or 6 for x )?

---

### Post by illmatic on 2007-07-02
well now everything worked besides starting the program
i installed everything u said but i dont know how to start the program cause if i double klick the *.rbw file nothing heppens :(

---

### Post by illmatic on 2007-07-04
cmon pls some help

---

### Post by illmatic on 2007-07-07
i only need to know this last thing ... so pls someone help

---

### Post by illmatic on 2007-07-08
i just need 1 answer pls ....

---

### Post by illmatic on 2007-07-10
pls just 1 answer -.-''

---

### Post by bclark on 2007-07-10
After installation you can start XDCC-Fetch by executing XDCC-Fetch.rbw

---

### Post by illmatic on 2007-07-11
now i get the following error:

alin@alin:~/Desktop/XDCC-Fetch$ ./XDCC-Fetch.rbw
+/usr/lib/ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- fox (LoadError)
        from /usr/lib/ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from ./src/GUI/Main_Window.rb:43
        from ./XDCC-Fetch.rbw:29:in `require'
        from ./XDCC-Fetch.rbw:29

i also dont know what to chose while 
executing 
sudo gem install xdcc-fetch

cause theres this big list
 1. fxruby 1.6.11 (ruby)
 2. fxruby 1.6.11 (mswin32)
 3. fxruby 1.6.10 (mswin32)
 4. fxruby 1.6.10 (ruby)
 5. fxruby 1.6.9 (mswin32)
 6. fxruby 1.6.9 (ruby)
 7. fxruby 1.6.8 (ruby)
 8. fxruby 1.6.8 (mswin32)
 9. fxruby 1.6.7 (mswin32)
 10. fxruby 1.6.7 (ruby)
 11. fxruby 1.6.6 (ruby)
 12. fxruby 1.6.6 (mswin32)
 13. fxruby 1.6.5 (mswin32)
 14. fxruby 1.6.5 (ruby)
 15. fxruby 1.6.4 (ruby)
 16. fxruby 1.6.4 (mswin32)
 17. fxruby 1.6.3 (mswin32)
 18. fxruby 1.6.3 (ruby)
 19. fxruby 1.6.2 (mswin32)
 20. fxruby 1.6.2 (ruby)
 21. fxruby 1.6.1 (mswin32)
 22. fxruby 1.6.1 (ruby)
 23. fxruby 1.6.0 (mswin32)
 24. fxruby 1.6.0 (ruby)
 25. fxruby 1.4.7 (ruby)
 26. fxruby 1.4.7 (mswin32)
 27. fxruby 1.4.6 (mswin32)
 28. fxruby 1.4.6 (ruby)
 29. fxruby 1.4.5 (mswin32)
 30. fxruby 1.4.5 (ruby)
 31. fxruby 1.4.4 (mswin32)
 32. fxruby 1.4.4 (ruby)
 33. fxruby 1.4.3 (mswin32)
 34. fxruby 1.4.3 (ruby)
 35. fxruby 1.4.2 (ruby)
 36. fxruby 1.4.2 (mswin32)
 37. fxruby 1.4.1 (ruby)
 38. fxruby 1.4.1 (mswin32)
 39. fxruby 1.4.0 (ruby)
 40. fxruby 1.2.6 (mswin32)
 41. fxruby 1.2.6 (ruby)
 42. fxruby 1.2.5 (ruby)
 43. fxruby 1.2.5 (mswin32)
 44. fxruby 1.2.4 (mswin32)
 45. fxruby 1.2.4 (ruby)
 46. fxruby 1.2.3 (ruby)
 47. fxruby 1.2.3 (mswin32)
 48. fxruby 1.2.2 (mswin32)
 49. fxruby 1.2.2 (ruby)
 50. fxruby 1.2.1 (mswin32)
 51. fxruby 1.2.1 (ruby)
 52. Cancel installation


i chose option 1...

---

### Post by illmatic on 2007-07-13
PLS I just wanna get this problem solved ...

---

### Post by illmatic on 2007-07-15
COME ON pls i just need a little help

---

### Post by illmatic on 2007-07-16
pls just one hint

---

### Post by illmatic on 2007-07-21
can nobody help me pls?

---

### Post by illmatic on 2007-07-23
nobody any idea?
if i type "./XDCC-Fetch.rbw"
and if i type "ruby XDCC-Fetch.rbw"
i get the following massage

/usr/lib/ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- fox (LoadError)
        from /usr/lib/ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from ./src/GUI/Main_Window.rb:43
        from XDCC-Fetch.rbw:29:in `require'
        from XDCC-Fetch.rbw:29

---

### Post by illmatic on 2007-07-26
cmon PLS PLS PLS

---

### Post by illmatic on 2007-07-28
pls just one hint

---

### Post by wishmechaos on 2007-10-27
sudo gedit /var/lib/gems/1.8/gems/XDCC-Fetch-1.409/src/GUI/Main_Window.rb

in lines 29-31 replace

require_gem 'fxruby', '>= 1.1.0'
require 'fox12'
require 'fox12/colors'

with

gem 'fxruby', '>= 1.1.0'
require 'fox16'
require 'fox16/colors'

XDCC-Fetch should really be upgraded to libfox1.6

cheers

---

### Post by Nio on 2007-11-01
I did what you said and i get the following error:

```

./src/GUI/Main_Window.rb:112:in `hitItem': Expected FXTreeItem * (TypeError)
        from ./src/GUI/Main_Window.rb:112:in `hit_rec'
        from ./src/GUI/Main_Window.rb:123:in `item_from_pos'
        from C:/Program Files/ruby/lib/ruby/gems/1.8/gems/fxruby-1.6.6-mswin32/l
ib/fox16/iterators.rb:189:in `each'
        from ./src/GUI/Main_Window.rb:122:in `item_from_pos'
        from ./src/GUI/Main_Window.rb:102:in `init_clickedItem'
        from C:/Program Files/ruby/lib/ruby/gems/1.8/gems/fxruby-1.6.6-mswin32/l
ib/fox16/responder2.rb:57:in `call'
        from C:/Program Files/ruby/lib/ruby/gems/1.8/gems/fxruby-1.6.6-mswin32/l
ib/fox16/responder2.rb:57:in `onHandleMsg'
        from ./src/GUI/Main_Window.rb:280:in `run'
        from ./src/GUI/Main_Window.rb:280
        from C:/Program Files/ruby/lib/ruby/site_ruby/1.8/rubygems/custom_requir
e.rb:27:in `gem_original_require'
        from C:/Program Files/ruby/lib/ruby/site_ruby/1.8/rubygems/custom_requir
e.rb:27:in `require'
        from XDCC-Fetch.rbw:29

```
I am on a windows machine though.

---

### Post by sofamensch on 2008-02-17
well.. you quite often spammed your own thread. not very helpful though :-)

It is possible to use Xdcc-Catcher (but only the FREE Version, Pro does not work for some reason) with WINE.
[www.xdcc-catcher.com](www.xdcc-catcher.com) .. but i guess you already know :-)

Otherwise.. stick with pages like packetnews.com and use a usual IRC Client with DCC capability

---

### Post by sofamensch on 2008-02-18
Okay but as i figured out the Free Version is quite featureless. 

Current try is to emulate WinXP with ttp://virtualbox.org/wiki/Downloads (like VMWare)

---

