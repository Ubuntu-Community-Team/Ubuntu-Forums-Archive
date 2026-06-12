---
title: "cant compile working code"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-03-07
im tring to compile this:
[I]
#include <iostream.h>

using namespace std;

int main() {
	cout << "hello world";
	return 0;	
}[/I]

Im using g++ (even tried gcc) in eclipse, and im getting lots of these

usr/include/c++/4.0.2/ostream:62: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’

I think theres some kind of library that it cant find. 

Does anyone know whats up?

---

### Post by gord on 2006-03-07
are you sure you have done ```
sudo apt-get install build-essential
```?

---

### Post by jinxjinx on 2006-03-07
Ok, when I compile w/ g++ all works great. What was in that thing that i needed?

But when i compile w/ gcc I getdiffernt errors, like this one:
main.cpp:6: undefined reference to `std::cout' what do you think is wrong?

Thanks a  lot!

---

