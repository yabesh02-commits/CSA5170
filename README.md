#include &lt;stdio.h&gt;
#include &lt;ctype.h&gt;
#include &lt;string.h&gt;
void encrypt(char* message, int key) {
for (int i = 0; message[i] != &#39;\0&#39;; ++i) {
char ch = message[i];
if (isalpha(ch)) {
char base = islower(ch) ? &#39;a&#39; : &#39;A&#39;;
ch = (ch - base + key) % 26 + base;
}
message[i] = ch;
}
}
int main() {
char message[1000];
int key;
printf(&quot;Enter a message: &quot;);
fgets(message, sizeof(message), stdin);
printf(&quot;Enter key (1-25): &quot;);
scanf(&quot;%d&quot;, &amp;key);
if (key &lt; 1 || key &gt; 25) {
printf(&quot;Invalid key! Must be between 1 and 25.\n&quot;);
return 1;
}
encrypt(message, key);
printf(&quot;Encrypted message: %s\n&quot;, message);
return 0;
}
