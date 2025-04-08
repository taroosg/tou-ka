<script lang="ts">
  let text = '';
  let textareaElement: HTMLTextAreaElement;

  function clearText(): void {
    text = '';
    if (textareaElement) {
      textareaElement.focus();
    }
  }

  function encodeText(text: string): string {
    return encodeURIComponent(text);
  }
</script>

<div class="h-dvh bg-gray-50 dark:bg-gray-900 p-4 sm:p-6 flex flex-col justify-center items-center">
  <div class="w-full max-w-lg mx-auto p-5 sm:p-7">

    <div class="mb-4 text-center">
      <h1 class="text-gray-900 dark:text-white text-xl">投下</h1>
    </div>

    <div class="mb-4">
      <textarea
        id="text"
        bind:value={text}
        bind:this={textareaElement}
        placeholder="投稿したいテキストを入力してボタンを押すと投稿画面に反映されます．&#13;未入力の場合は投稿画面が空欄で表示されます．"
        class="w-full px-4 py-3 border border-gray-300 dark:border-gray-700 focus:outline-none focus:border-blue-500 bg-gray-50 dark:bg-gray-900 dark:text-white resize-none h-36 text-base"
      ></textarea>
    </div>

    <div class="mb-4 flex justify-center">
      <button
        on:click={clearText}
        class="text-xs py-2 px-2 text-gray-900 dark:text-white font-normal text-center transition-colors text-base hover:bg-gray-100 dark:hover:bg-gray-800"
      >
        🗑️
      </button>
    </div>

    <div class="flex flex-col gap-4">
      <a
        href="https://twitter.com/intent/tweet?text={encodeText(text)}"
        target="_blank"
        class="py-3 px-5 text-gray-900 dark:text-white font-normal text-center transition-colors text-base border border-gray-300 dark:border-gray-700"
      >
        Tweet
      </a>
      <a
        href="https://www.threads.net/intent/post?text={encodeText(text)}"
        target="_blank"
        class="py-3 px-5 text-gray-900 dark:text-white font-normal text-center transition-colors text-base border border-gray-300 dark:border-gray-700"
      >
        Threads に投稿
      </a>
      <a
        href="https://bsky.app/intent/compose?text={encodeText(text)}"
        target="_blank"
        class="py-3 px-5 text-gray-900 dark:text-white font-normal text-center transition-colors text-base border border-gray-300 dark:border-gray-700"
      >
        Bluesky に投稿
      </a>
    </div>
  </div>
</div>
