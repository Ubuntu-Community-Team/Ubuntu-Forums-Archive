---
title: "New User Ruby Question"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by kristiaan_d on 2007-02-16
Hi All,
im new to the forum and new to linux as well, my complete understanding of linux is this

switch on
logon
create / rename / delete / chmod - files or folders
logoff / shutdown

i have always been a windows user from way back when, but now i need to install linux, thanks to ubuntu that was increadably pain free and easy however i now need to install Ruby on Rails etc for a project.

so far this is what i think i have done.

installed Dapper Drake Ubuntu distro of linux.

installed Ruby ( got loads of errors )
installed Rails ( again loads of errors )
installed Ruby Gems ( these did`nt work or failed to load or generated a cryptic message)

i have managed to install the base Apache2 system but this was done through Sybiotic package manager, so i knew it would work fine, i have tested it and it serves pages.

my question(s) is 

can someone please point me in the direction of a very simple to understand easy to read HOWTO of doing a complete installation of Ruby, rails, rubygems etc using apache2. oh and mysql for it as well.

plus how do i test this system once its installed ??? as i have no way of knowing if what i have done is working or not?!?!?!

this is the first link i tried to get it installed and it just seemed to fail all the time at different points

[http://www.urbanpuddle.com/articles/2006/06/10/install-ruby-rails-on-ubuntu-dapper-drake](http://www.urbanpuddle.com/articles/2006/06/10/install-ruby-rails-on-ubuntu-dapper-drake)

---

### Post by Jussi Kukkonen on 2007-02-16
It's been a while since I tried Ruby, but ...

> installed Ruby ( got loads of errors )
installed Rails ( again loads of errors )
installed Ruby Gems ( these did`nt work or failed to load or generated a cryptic message)
More details, please. Ruby and Rails should be available in the repositories... Gems should be easily installable after you have ruby working.

> 
plus how do i test this system once its installed ??? as i have no way of knowing if what i have done is working or not?!?!?!
Searching for "Ruby tutorial" on Google should give you dozens of alternatives. They shouldn't be hard to find. A "Hello world" goes like this:

Save this to *rubytest.rb*
```
#!/usr/bin/ruby
print "Hello World\n"
```
Then run
```
chmod +x rubytest.rb
./rubytest.rb
```
It should output "Hello World"

---

### Post by kristiaan_d on 2007-02-19
Hi Jussi,
i found a tutorial on installing ruby eventually turns out there is a great tutorial on this site, 

[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

i followed this and got no errors what so ever during the installation of anything mentioned in the howto.

i tried your code:

and it worked first time, thanks for the information regarding this, much appreciated.

thanks
Kris

---

