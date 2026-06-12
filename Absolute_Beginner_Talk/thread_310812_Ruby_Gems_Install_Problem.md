---
title: "Ruby Gems Install Problem"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by the gnome on 2006-12-01
Hi, I compiled Ruby 1.8.5 from source with no major problems.  I then downloaded the latest Rubygems and tried to get that installed and all heck broke loose.

I ran this from downloaded gems:
sudo ruby setup.rb

Which gave the following error:
```
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- zlib (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:9
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/builder.rb:7
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:93:in `manage_gems'
        from /usr/local/bin/gem:10

```

I did some research and some suggested checking that zlib was installed, and it is.  I've installed using this method under debian without issue, not sure what's going on here.

I'm pretty lost on this one.

---

### Post by alakra on 2007-01-24
I know this is an old post, but I will go ahead an answer this one.

Do this:

```
sudo apt-get install zlib1g-dev
```

Then recompile ruby's zlib library from the 1.8.5 ruby tarball:

```
sudo ruby /where_ever_you_extracted_Ruby/ext/zlib/extconf.rb
```

I don't know if this is necessary, but I did this anyway:

```
sudo make
sudo make install
```

Then try recompiling rubygems again.

---

### Post by ibrudiiv on 2007-02-06
I wasn't the one that started this thread but this solution worked for me.

Thanks alakra.

---

