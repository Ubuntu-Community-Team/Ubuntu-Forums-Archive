---
title: "Some help with installed libraries :("
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by lobo-tuerto on 2008-01-02
Hello guys,

I have a problem that I think started after I upgraded my rubygems. All the
gems I had installed where gone.

Issuing this command showed an empty list:
"gem list" or "sudo gem list"


But I was sure I had rails, mongrel, sqlite3, rake and other gems
installed. So I did a "find / -name "mongrel*.*" and found them in:
/var/lib/gems/1.8/gems

After typing "gem env" I got this:
RubyGems Environment:
  - RUBYGEMS VERSION: 1.0.1 (1.0.1)
  - RUBY VERSION: 1.8.6 (2007-06-07 patchlevel 36) [i486-linux]
  - INSTALLATION DIRECTORY: /usr/lib/ruby/gems/1.8
  - RUBY EXECUTABLE: /usr/bin/ruby1.8
  - RUBYGEMS PLATFORMS:
    - ruby
    - x86-linux
  - GEM PATHS:
     - /usr/lib/ruby/gems/1.8
  - GEM CONFIGURATION:
     - :update_sources => true
     - :verbose => true
     - :benchmark => false
     - :backtrace => false
     - :bulk_threshold => 1000
  - REMOTE SOURCES:
     - [http://gems.rubyforge.org](http://gems.rubyforge.org)


So the problem it seems, is that the old directory was:
/var/lib/gems/1.8/gems

And the new one is:
/usr/lib/ruby/gems/1.8/gems

So how do I tell RubyGems to look in the old directories? and why did
the directories change? do you think something else could be broken with
my installation? how can I prevent this from happening again?

Who does save things to /var, and who does save things to /usr?


Thanks in advance.

---

### Post by nathandelane on 2008-01-02
Did you try this?

```
gem list --local
```

The --local directive tells gem to look at your local repository.

Nathan

---

### Post by lobo-tuerto on 2008-01-03
I was listing the local gems.


The problem it seems was that I did used apt-get to install rubygems, then did a "sudo gem update --system" and that messed the gem libraries up.

I had to remove rubygems with apt-get and do a manual install, now all seems to be working more or less ok. :neutral:

---

### Post by nathandelane on 2008-01-03
That's good to hear - I would never use apt to install gems personally - same thing with python - I'd never use apt to install python modules. In Ruby, gem is the preferred tool to install gems - do gem install *gemname*.  Like in python, unless you have to compile a module separately for some reason (I've had to), use CPAN. Just seems right to me.  Good luck.  You may want to try uninstalling Ruby all together and start fresh with installing it, and use gem to install your gems. :)

Nathan

---

