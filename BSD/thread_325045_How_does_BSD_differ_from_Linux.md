---
title: "How does BSD differ from Linux?"
date: 2006-12-24
forum: BSD
---

### Post by gwilson on 2006-12-24
I know that Linux and BSD are both offshoots of Unix, but how similar are BSD and Linux? I just found out that a potential employer's product is based on a customized version of Free BSD and wondered how similar Free BSD would be to Linux.  Are we mainly talking syntax when issuing command in terminal mode, or is it a completely different kettle of fish?

Any idea what sorts of things would be better done in BSD than in Linux? Any reason for choosing Free BSD over Linux, or is it likely that the developer just happened to know BSD when he designed the product?

Thanks.

---

### Post by Hendrixski on 2006-12-24
That's a good question.  I think BSD is a UNIX.  Though 'freeBSD' is not, it's a unix-clone. There's actually some official governing body that determines what is and what isn't a UNIX.  Like apple has submited OSX to be officially a UNIX, since it is BSD-based.

The difference is most likely just the kernel.  Though I'd be interested to know more!

---

### Post by Phatfiddler on 2006-12-24
If i remember right, BSD is under a different license than GPL that allows the code to not only be modified, but used for commercial purposes i.e. OSX.  By basing his product on BSD, the license allows him to "close it up" and re-sell it as his own product.

---

### Post by RAV TUX on 2006-12-25
moving to the BSD forum


> 
The text of the license is considered to be in the [public domain]("http://en.wikipedia.org/wiki/Public_domain") and thus may be modified without restriction.


* Copyright (c) <year>, <copyright holder>
* All rights reserved.
* Redistribution and use in source and binary forms, with or without
* modification, are permitted provided that the following conditions are met:
*
*     * Redistributions of source code must retain the above copyright
*       notice, this list of conditions and the following disclaimer.
*     * Redistributions in binary form must reproduce the above copyright
*       notice, this list of conditions and the following disclaimer in the
*       documentation and/or other materials provided with the distribution.
*     * Neither the name of the <organization> nor the
*       names of its contributors may be used to endorse or promote products
*       derived from this software without specific prior written permission.
*
* THIS SOFTWARE IS PROVIDED BY THE REGENTS AND CONTRIBUTORS ``AS IS'' AND ANY
* EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
* WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
* DISCLAIMED. IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE FOR ANY
* DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
* (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
* LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
* ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
* (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
* SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.[http://en.wikipedia.org/wiki/BSD/License](http://en.wikipedia.org/wiki/BSD/License)

---

### Post by mushroom on 2006-12-25
I wish I had the ability to reword the LGPL as succinctly, so I could just pop it into the beginning of a source file.

BSD is a completely different kernel. The low-level userland tools (the shell, compiler, etc.) are different as well. Beyond that, you get pretty much the same user experience, minus Flash and some other proprietary things. Binary compatibility with Linux is really good, or so I'm told.

---

### Post by mips on 2006-12-25
When you refer to Linux in essence it refers to the Kernel only, linux is just the kernel. BSD on the other hand is the entire os as whole including the kernel and is developed as such.

---

