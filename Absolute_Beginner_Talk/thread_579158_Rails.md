---
title: "Rails"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by rgreen on 2007-10-18
I have installed ruby, rails and rubygems. how do I update rails to the latest version? I get the folling error when I try gem update rails.user@ubuntu704desktop:~$ gem update rails
/usr/local/lib/ruby/1.8/i686-linux/digest/md5.so: libcrypto.so.4: cannot open shared object file: No such file or directory - /usr/local/lib/ruby/1.8/i686-linux/digest/md5.so (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/gems/1.8/gems/rubygems-update-0.9.4/lib/rubygems/package.rb:10
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:32:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:32:in `require'
        from /usr/local/lib/ruby/gems/1.8/gems/rubygems-update-0.9.4/lib/rubygems/builder.rb:7
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:32:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:32:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:110:in `manage_gems'
        from /usr/local/bin/gem:10

---

### Post by timetunnel on 2007-10-18
Do you have rails installed out of the ubuntu respository, or did you install it with "gem" initially?

---

### Post by rgreen on 2007-10-20
Both.

---

### Post by timetunnel on 2007-10-20
Hm.. I'm not sure but some ideas: the paths in the error message point to a places  /usr/**local**/lib  and /usr/**local**/bin. These are **not**  the places where "rubygems" is installed to by the ubuntu package "rubygems". It usualy goes to "/usr/bin" and "/usr/lib/ruby". 

My rails setup is as follows and it works:
[LIST]
[*]only "ruby", "rdoc", "ri", "irb" and "rubygems" are installed out of the ubuntu repository. **No other** ruby packages from the ubuntu repository are installed
[*]"rails" and "rake" are installed using "_[B]sudo[/B_] gem install...."
[/LIST]

If "rubygems" is installed out of the ubuntu repository, you have to run it as superuser. All files installed by "gem install" will go to "/var/lib/gems".

It might be a good idea to uninstall all ruby and ruby-related packages, delete all files the were installed with "gem install", clean up system variables you might have changed for ruby and start from scratch (like I described above)

Jens

---

