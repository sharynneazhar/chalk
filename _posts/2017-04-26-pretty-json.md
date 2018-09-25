---
layout: post
title: "Pretty JSON"
tags: [javascript, webdev]
---

I first learned about the `JSON.stringify()` method from a senior developer during an internship. Since then, I've used it A LOT to debug JS code, but one thing that always annoyed me was how it prints the whole JSON object in one long line.

I spent a good 30 minutes or so looking at different Stack Overflow solutions. Through combinations of googling bad keywords and lazy skimming, I found a <s>good</s> great solution.

The answer is in the [documentation][1]. Duh, why didn't I think of that in the first place?

The native `JSON.stringify()` method has a built-in option to format readable output. Here's the syntax:

{% highlight js %}
JSON.stringify(value[, replacer[, space]])
{% endhighlight %}

The first parameter `value` is the value you want to convert to a JSON string. The second parameter `replacer` is basically a filtering function you can pass in to ignore certain values. The third parameter `space` is the golden ticket. It is a String or Number object that is used to insert whitespace into the output.

Example:

{% highlight js %}
var myObj = {"foo": "bar", "nums": [{"one": 1, "uno": 1}, {"two": 2}]};
JSON.stringify(myObj, null, 2);
{% endhighlight %}


Output:

{% highlight json %}
{
  "foo": "bar",
  "nums": [
    {
      "one": 1,
      "uno": 1
    },
    {
      "two": 2
    }
  ]
}
{% endhighlight %}

Aha!

[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify
