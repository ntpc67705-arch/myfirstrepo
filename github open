import streamlit as st

st.set_page_config(page_title="AI 遊戲指令發射台", layout="centered")

st.title("🎮 AI 遊戲指令發射台")
st.subheader("SDD (Spec-Driven Development) 規格產生器")

with st.form("game_form"):
    # 1. 主題
    theme = st.radio("1. 選擇你的遊戲主題：", 
                    ["賽博龐克 (Cyberpunk)", "奇幻冒險 (Fantasy)", "驚悚實驗室 (Horror Lab)", "復古 8-bit (Retro)", "其他（請在下方輸入）"])
    custom_theme = st.text_input("自定義主題（若選擇其他）：")

    # 2. 玩法
    gameplay = st.radio("2. 選擇核心玩法：", 
                       ["文字冒險 (Adventure)", "瘋狂點擊 (Clicker)", "猜謎解鎖 (Riddle)", "生存挑戰 (Survival)", "其他（請在下方輸入）"])
    custom_gameplay = st.text_input("自定義玩法（若選擇其他）：")

    # 3. AI 個性
    narrator = st.radio("3. AI 指導員的個性：", 
                       ["毒舌酸民 (Toxic)", "熱血教官 (Enthusiastic)", "神祕黑客 (Mysterious)", "冷酷機器人 (Logical)", "其他（請在下方輸入）"])
    custom_narrator = st.text_input("自定義個性（若選擇其他）：")

    # 4. 輸贏條件
    win_loss = st.radio("4. 輸贏條件：", 
                       ["生命值 (HP) 歸零", "計時器 (Timer) 結束", "積分 (Score) 達標", "其他（請在下方輸入）"])
    custom_win_loss = st.text_input("自定義條件（若選擇其他）：")

    # 5. 驚喜元素
    twist = st.radio("5. 加入隨機驚喜：", 
                    ["隨機寶箱 (Random Loot)", "背景天氣變色 (Weather)", "隱藏彩蛋 (Easter Egg)", "其他（請在下方輸入）"])
    custom_twist = st.text_input("自定義驚喜（若選擇其他）：")

    submit = st.form_submit_button("🚀 生成開發規格 (Spec Prompt)")

if submit:
    # 整合答案
    final_theme = custom_theme if theme == "其他（請在下方輸入）" else theme
    final_gameplay = custom_gameplay if gameplay == "其他（請在下方輸入）" else gameplay
    final_narrator = custom_narrator if narrator == "其他（請在下方輸入）" else narrator
    final_win_loss = custom_win_loss if win_loss == "其他（請在下方輸入）" else win_loss
    final_twist = custom_twist if twist == "其他（請在下方輸入）" else twist

    # 生成 Meta-Prompt
    master_prompt = f"""
你是一位專業的「遊戲架構師」與「Streamlit 開發專家」。請根據以下規格，為我產出一份專業的 `spec.md` 檔案，以便讓 Codex 寫出 Python 程式碼。

### 學生創意輸入：
1. 主題：{final_theme}
2. 玩法：{final_gameplay}
3. 個性：{final_narrator}
4. 輸贏：{final_win_loss}
5. 驚喜：{final_twist}

### `spec.md` 必須包含的技術規格：
- 使用 Streamlit 框架，必須使用 `st.session_state` 管理遊戲狀態（如 HP、分數、場景）。
- 根據【主題】設計專屬 CSS 樣式。
- 根據【個性】設定 AI 提示詞語氣。
- 實作完整遊戲循環（初始化 -> 互動 -> 狀態更新 -> 渲染）。
- 必須包含視覺回饋（例如背景變色或 Emoji 動畫）。

請直接輸出 Markdown 格式的規格書內容。
"""
    st.success("✅ 指令已生成！請複製下方文字並貼給 AI。")
    st.code(master_prompt, language="markdown")