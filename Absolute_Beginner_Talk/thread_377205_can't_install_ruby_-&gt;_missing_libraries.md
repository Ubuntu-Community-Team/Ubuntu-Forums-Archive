---
title: "can't install ruby -&gt; missing libraries"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2007-03-05
> 
chris@chris-laptop:~/Desktop/rubygems-0.9.2/rubygems-0.9.0$ sudo ruby setup.rb 
setup.rb:52:in `require': no such file to load -- rbconfig (LoadError)
        from setup.rb:52



does anyone know what is missing to give me this error?  I should rephrase this..does anyone know where the rbconfig.rb file is supposed to be, and even better what libraries are missing to cause this.

Thanks

---

### Post by chris.olsen on 2007-03-05
I have tried re-installing ruby, but I still have the same problem.

This is killin' me

---

### Post by Jessehk on 2007-03-06
It does not appear that you are installing Ruby the language, but rather the package manager for its libraries (rubygems).

If you want to insall Ruby, simply:
```

sudo aptitude install ruby irb rdoc ri

```

You should then be able to install rubygems as you are attempting to now.

---

### Post by chris.olsen on 2007-03-06
Sorry I should've closed this thread.  I had to re-install the rubylib files.  It seems that some of them were missing.

Your help is appreciated.

---

