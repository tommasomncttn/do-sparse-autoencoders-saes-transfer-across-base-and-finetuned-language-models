
![[Pasted image 20250207144943.png]]Remove the highlighted text, I think it's too trivial to mention (and we don't have a citation anyway)
![[Pasted image 20250207145044.png]]
Remove this footnote #3 - I write that it's non-standard here and now I would add that it's just silly, so no need to include it...

![[Pasted image 20250207145221.png]]
(Optional) I noticed that some of the points here overlap with the previous section 1.1, e.g. I write that 
- "The model can perform the computation because it’s genuinely trained to perform the task well, or because it learned that doing the task well correlates with its other learned goals like gaining more power and resources. Without understanding the computation, we have no direct way of distinguishing between the two." and 
- "Ultimately we want to say that a model doesn't implement some class of behaviors. Enumerating over all features makes it easy to say a feature doesn't exist (e.g. "there is no 'deceptive behavior' feature") but that isn't quite what we want. We expect models that need to represent the world to represent unsavory behaviors. But it may be possible to build more subtle claims such as "**all 'deceptive behavior' features do not participate in circuits X, Y and Z.**”

I think the paragraph still adds a good amount of new information (especially in terms of useful references), but maybe it could be rephrased to avoid duplicate takes.

![[Pasted image 20250207145459.png]]
>base and finetuned ***models***

Currently it's as if the last word is missing here^

![[Pasted image 20250207145547.png]]
Add a clarification at the end of the paragraph: 
>...we also made a parallel coordinate plot **(below we show two versions of the same plot: with different density ranges highlighted)**

![[Pasted image 20250207145627.png]]
Edit (in bold): 
>And if we assume that some kind of circuit analysis has been done for the base model to prove that **it doesn't implement certain undesirable behaviors**

And **remove the footnote #7**.

![[Pasted image 20250207145807.png]]
We should integrate this edit into the main text:
>~~So if we accept the logit weights effect as a good proxy for the “feature’s downstream effect”, it means that our small fraction of regular features that transfer to the finetuned model (with respect to the activation similarity score) have similar downstream effects too.
~~
**However, we realized** that it's easy to be misled by the mean logits similarity score. What it's really saying is that our unembedding matrix (which is multiplied by the feature direction to get the logits similarity) hasn't changed that much after finetuning (with a Frobenius norm ratio equal to 1.117 as we checked for our Gemma finetune). So **if the feature has still the same direction**, we can indeed say that the "direct feature effect" hasn't changed in the finetuned model, but **we never checked this premise!** All we know is that there exist ~10% of features which have reasonably high activation similarity scores with the features from the base model. **The key point is that the latter is a statement about the feature's encoder direction** (one that is used to project onto to get the feature's activation, [explained by Neel Nanda here](https://www.lesswrong.com/posts/fKuugaxt2XLTkASkk/open-source-replication-and-commentary-on-anthropic-s)), **not the decoder one -** which is what we mean when we talk about **feature directions**. So it could be the case that the feature is still there but _**changed its direction**_ as discussed in [this comment,](https://www.lesswrong.com/posts/bsXPTiAhhwt5nwBW3/do-sparse-autoencoders-saes-transfer-across-base-and?commentId=pJHfoZ2GLD8neS57g) it could also be that some features change their directions and the others don't - it's impossible to tell when the reconstruction score (e.g. variance explained) is as poor as in the Gemma-2b case.
