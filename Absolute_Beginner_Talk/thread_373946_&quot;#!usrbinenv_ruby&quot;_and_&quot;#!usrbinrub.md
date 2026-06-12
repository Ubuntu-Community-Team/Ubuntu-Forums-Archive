---
title: "&quot;#!/usr/bin/env ruby&quot; and &quot;#!/usr/bin/ruby&quot;"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-03-01
What is the difference between

#!/usr/bin/env ruby

and 

#!/usr/bin/ruby

?

Also, what is the first line that tells the script what to use called?

---

### Post by dmsynck on 2007-03-16
The difference is that by using #! /usr/bin/env ruby as opposed to 
#! /usr/bin/ruby you do not have to hard-code the path information to the ruby binary or include the ruby version number i.e #!/ usr/bin/ruby1.8. As long as ruby is in one of the directories in your PATH, env will know where to find it. 
This first line is generally called a "Shebang" line.

---

