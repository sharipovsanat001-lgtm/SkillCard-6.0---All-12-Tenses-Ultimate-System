<!DOCTYPE html>
<html lang="uz">
<head> 
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
    <title>SkillCard 6.0 - All 12 Tenses Ultimate System</title>  
    <style>       
    

        
        * {       
            margin: 0;  
            padding: 0; 
            box-sizing: border-box;  
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;  
        }
 
        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #0f172a 0%, #1e1b4b 50%, #311042 100%);
            color: #f8fafc; 
            display: flex; 
            flex-direction: column;
            align-items: center;
            padding: 2rem;
        }

        header {
            text-align: center;
            margin-bottom: 2.5rem;
        }

        header h1 {
            font-size: 2.5rem;
            font-weight: 800;
            background: linear-gradient(to right, #38bdf8, #c084fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 0.5rem;
        }

        .container {
            width: 100%;
            max-width: 1000px;
            display: flex;
            flex-direction: column;
            gap: 2rem;
        }

        .panel {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
        }

        .panel h3 {
            color: #38bdf8;
            margin-bottom: 1.2rem;
        }

        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin-bottom: 1rem;
        }

        input, select {
            width: 100%;
            background: rgba(15, 23, 42, 0.6);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 0.8rem 1.2rem;
            color: #fff;
            font-size: 1rem;
        }

        button {
            background: linear-gradient(135deg, #38bdf8 0%, #818cf8 100%);
            color: #0f172a;
            border: none;
            border-radius: 12px;
            padding: 0.8rem 1.8rem;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 0 20px rgba(56, 189, 248, 0.5);
        }

        .filter-panel {
            display: flex;
            gap: 1rem;
        }

        .filter-btn {
            background: rgba(255, 255, 255, 0.05);
            color: #94a3b8;
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 0.6rem 1.2rem;
            border-radius: 30px;
            cursor: pointer;
        }

        .filter-btn.active {
            background: linear-gradient(135deg, #c084fc 0%, #6366f1 100%);
            color: #fff;
        }

        .day-box {
            background: rgba(255, 255, 255, 0.01);
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 1.5rem;
            margin-bottom: 2rem;
        }

        .day-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            padding-bottom: 0.8rem;
            margin-bottom: 1.5rem;
        }

        .day-date { font-size: 1.3rem; color: #c084fc; font-weight: 700; }
        .day-topic { background: rgba(56, 189, 248, 0.15); color: #38bdf8; padding: 0.3rem 0.8rem; border-radius: 15px; font-size: 0.9rem; font-weight: 600; }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 1.5rem;
            margin-bottom: 1.5rem;
        }

        .flashcard { height: 140px; perspective: 1000px; cursor: pointer; }
        .card-inner { position: relative; width: 100%; height: 100%; transition: transform 0.5s; transform-style: preserve-3d; }
        .flashcard.flipped .card-inner { transform: rotateY(180deg); }
        .card-front, .card-back { position: absolute; width: 100%; height: 100%; -webkit-backface-visibility: hidden; backface-visibility: hidden; border-radius: 15px; padding: 1rem; display: flex; justify-content: center; align-items: center; text-align: center; }
        .card-front { background: rgba(255,255,255,0.03); border: 1px solid rgba(56, 189, 248, 0.2); }
        .card-back { background: rgba(192, 132, 252, 0.05); border: 1px solid rgba(192, 132, 252, 0.2); transform: rotateY(180deg); color: #e9d5ff; }

        .test-section { background: rgba(15, 23, 42, 0.5); border-radius: 15px; padding: 1.5rem; margin-top: 1.5rem; }
        .test-card { background: rgba(255,255,255,0.02); border: 1px solid rgba(255,255,255,0.05); padding: 1rem; border-radius: 12px; margin-bottom: 1rem; }
        .options-layout { display: grid; grid-template-columns: 1fr 1fr; gap: 0.5rem; margin-top: 0.8rem; }
        
        .opt-btn {
            background: rgba(255,255,255,0.05); color: #fff; border: 1px solid rgba(255,255,255,0.1);
            padding: 0.6rem; border-radius: 8px; cursor: pointer; text-align: left; transition: background 0.2s;
        }
        .opt-btn.correct { background: rgba(34, 197, 94, 0.35) !important; border-color: #22c55e !important; color: #22c55e; font-weight: 600; }
        .opt-btn.wrong { background: rgba(239, 68, 68, 0.35) !important; border-color: #ef4444 !important; color: #ef4444; font-weight: 600; }

        .empty-state { text-align: center; padding: 3rem; color: #64748b; border: 2px dashed rgba(255, 255, 255, 0.05); border-radius: 20px; }
    </style>
</head>
<body>

    <header>
        <h1>SkillCard 6.0 Ultimate</h1>
        <p>12 zamon to'liq bazasi va 100% Ishlaydigan Interaktiv Test Tizimi</p>
    </header>

    <div class="container">
        
        <section class="panel">
            <h3>📅 Kunlik dars va Mavzuni tanlang</h3>
            <div class="form-grid">
                <div>
                    <label style="font-size:0.85rem; color:#94a3b8;">Sanani tanlang (Kalendar):</label>
                    <input type="date" id="main-date" required>
                </div>
                <div>
                    <label style="font-size:0.85rem; color:#94a3b8;">Mavzuni (Zamonni) tanlang:</label>
                    <select id="main-topic"></select>
                </div>
            </div>
            
            <div style="border-top: 1px dashed rgba(255,255,255,0.1); padding-top:1rem; margin-top:1rem;">
                <p style="font-size:0.9rem; color:#94a3b8; margin-bottom:0.5rem;">💡 Ushbu dars kungi yodlash kartochkalari (Ixtiyoriy):</p>
                <div class="form-grid" style="grid-template-columns: 1fr 1fr;">
                    <input type="text" id="card-q" placeholder="Inglizcha gap (Masalan: I have done it)">
                    <input type="text" id="card-a" placeholder="O'zbekcha tarjimasi (Masalan: Men buni qildim)">
                </div>
            </div>
            
            <button type="button" id="generate-day-btn" style="width:100%; margin-top:0.5rem; background: linear-gradient(135deg, #38bdf8 0%, #818cf8 100%); color:#0f172a;">
                ⚡ Dars kunini yaratish va 15 talik testni avtomatik tuzish
            </button>
        </section>

        <div class="filter-panel">
            <button class="filter-btn active" id="f-all">Hamma kunlar</button>
            <button class="filter-btn" id="f-today">Faqat bugungi kun</button>
        </div>

        <main id="timeline"></main>
    </div>

    <script>
        // --- INGLIZ TILIDAGI BARCHA 12 TA ZAMON VA 15 TADAN JAMI 180 TA TEST BAZASI ---
        const autoTestDatabase = {
            "Present Simple": [
                { q: "She ___ (live) in Tashkent.", o: ["lives", "live", "living", "lived"], c: "lives" },
                { q: "We ___ (not/work) on Sundays.", o: ["don't work", "doesn't work", "not work", "aren't work"], c: "don't work" },
                { q: "___ you play football every day?", o: ["Do", "Does", "Is", "Are"], c: "Do" },
                { q: "He always ___ (get up) early.", o: ["gets up", "get up", "getting up", "got up"], c: "gets up" },
                { q: "My brother ___ (not/like) milk.", o: ["doesn't like", "don't like", "isn't like", "not likes"], c: "doesn't like" },
                { q: "Where ___ they live?", o: ["do", "does", "is", "are"], c: "do" },
                { q: "Cats ___ (catch) mice.", o: ["catch", "catches", "catching", "caught"], c: "catch" },
                { q: "Water ___ (freeze) at 0°C.", o: ["freezes", "freeze", "freezing", "froze"], c: "freezes" },
                { q: "___ your father work here?", o: ["Does", "Do", "Is", "Are"], c: "Does" },
                { q: "I ___ (not/know) the answer.", o: ["don't know", "doesn't know", "not know", "am not know"], c: "don't know" },
                { q: "She ___ (study) German on Mondays.", o: ["studies", "studys", "study", "studying"], c: "studies" },
                { q: "They ___ (go) to the gym twice a week.", o: ["go", "goes", "going", "went"], c: "go" },
                { q: "Do you like pizza? Yes, I ___.", o: ["do", "like", "does", "am"], c: "do" },
                { q: "It ___ (rain) a lot in autumn.", o: ["rains", "rain", "raining", "rained"], c: "rains" },
                { q: "What time ___ the train leave?", o: ["does", "do", "is", "has"], c: "does" }
            ],
            "Present Continuous": [
                { q: "I ___ (write) an email right now.", o: ["am writing", "is writing", "are writing", "write"], c: "am writing" },
                { q: "Listen! Someone ___ (sing).", o: ["is singing", "are singing", "sings", "am singing"], c: "is singing" },
                { q: "They ___ (not/watch) TV at the moment.", o: ["aren't watching", "isn't watching", "don't watch", "not watching"], c: "aren't watching" },
                { q: "___ you ___ (listen) to me now?", o: ["Are/listening", "Do/listen", "Is/listening", "Am/listening"], c: "Are/listening" },
                { q: "She ___ (cook) dinner in the kitchen currently.", o: ["is cooking", "are cooking", "cooks", "cooking"], c: "is cooking" },
                { q: "Look! The boys ___ (run).", o: ["are running", "is running", "run", "running"], c: "are running" },
                { q: "Why ___ he ___ (laugh) at the moment?", o: ["is/laughing", "are/laughing", "does/laugh", "is/laugh"], c: "is/laughing" },
                { q: "I ___ (not/sleep) right now.", o: ["am not sleeping", "isn't sleeping", "don't sleep", "not sleeping"], c: "am not sleeping" },
                { q: "The dog ___ (bark) outside at present.", o: ["is barking", "are barking", "barks", "barking"], c: "is barking" },
                { q: "___ it ___ (snow) heavily now?", o: ["Is/snowing", "Are/snowing", "Does/snow", "Is/snow"], c: "Is/snowing" },
                { q: "We ___ (have) a great time today.", o: ["are having", "is having", "have", "having"], c: "are having" },
                { q: "Where ___ they ___ (go) so fast?", o: ["are/going", "is/going", "do/go", "are/go"], c: "are/going" },
                { q: "He ___ (not/drive) his car today.", o: ["isn't driving", "aren't driving", "doesn't drive", "not driving"], c: "isn't driving" },
                { q: "Look at them! They ___ (dance) together.", o: ["are dancing", "is dancing", "dance", "dancing"], c: "are dancing" },
                { q: "I ___ (try) to study, please be quiet.", o: ["am trying", "is trying", "try", "trying"], c: "am trying" }
            ],
            "Present Perfect": [
                { q: "I ___ (lose) my keys. I can't find them.", o: ["have lost", "has lost", "lost", "lose"], c: "have lost" },
                { q: "___ you ever ___ (be) to London?", o: ["Have/been", "Has/been", "Did/be", "Were/been"], c: "Have/been" },
                { q: "She ___ (already/finish) her homework.", o: ["has already finished", "have already finished", "already finished", "is finished"], c: "has already finished" },
                { q: "We ___ (not/see) him today.", o: ["haven't seen", "hasn't seen", "didn't see", "don't see"], c: "haven't seen" },
                { q: "He ___ (live) here since 2015.", o: ["has lived", "have lived", "lived", "is living"], c: "has lived" },
                { q: "They ___ (just/arrive) at the station.", o: ["have just arrived", "has just arrived", "just arrived", "are just arriving"], c: "have just arrived" },
                { q: "How many books ___ you ___ (write)?", o: ["have/written", "has/written", "did/write", "do/write"], c: "have/written" },
                { q: "John ___ (not/call) me yet.", o: ["hasn't called", "haven't called", "didn't call", "doesn't call"], c: "hasn't called" },
                { q: "Everything is clean. I ___ (wash) the dishes.", o: ["have washed", "has washed", "washed", "washing"], c: "have washed" },
                { q: "___ she ___ (tell) you the news?", o: ["Has/told", "Have/told", "Did/tell", "Is/telling"], c: "Has/told" },
                { q: "We are not hungry. We ___ (just/eat).", o: ["have just eaten", "has just eaten", "just ate", "eat"], c: "have just eaten" },
                { q: "It ___ (stop) raining, so we can go out.", o: ["has stopped", "have stopped", "stopped", "is stopping"], c: "has stopped" },
                { q: "Nobody ___ (ever/climb) this mountain.", o: ["has ever climbed", "have ever climbed", "ever climbed", "is ever climbing"], c: "has ever climbed" },
                { q: "___ they ___ (decide) what to do?", o: ["Have/decided", "Has/decided", "Did/decide", "Are/deciding"], c: "Have/decided" },
                { q: "I ___ (know) her for ten years.", o: ["have known", "has known", "knew", "know"], c: "have known" }
            ],
            "Present Perfect Continuous": [
                { q: "I ___ (work) here for five hours.", o: ["have been working", "has been working", "am working", "worked"], c: "have been working" },
                { q: "She ___ (cough) all morning.", o: ["has been coughing", "have been coughing", "is coughing", "coughed"], c: "has been coughing" },
                { q: "Why are your clothes wet? ___ you ___ (swim)?", o: ["Have/been swimming", "Has/been swimming", "Are/swimming", "Did/swim"], c: "Have/been swimming" },
                { q: "They are tired. They ___ (travel) all day.", o: ["have been traveling", "has been traveling", "are traveling", "traveled"], c: "have been traveling" },
                { q: "It ___ (rain) since last night.", o: ["has been raining", "have been raining", "is raining", "rained"], c: "has been raining" },
                { q: "He is out of breath. He ___ (run).", o: ["has been running", "have been running", "is running", "ran"], c: "has been running" },
                { q: "How long ___ you ___ (learn) English?", o: ["have/been learning", "has/been learning", "are/learning", "did/learn"], c: "have/been learning" },
                { q: "We ___ (not/live) here for very long.", o: ["haven't been living", "hasn't been living", "aren't living", "didn't live"], c: "haven't been living" },
                { q: "Your eyes are red. ___ you ___ (cry)?", o: ["Have/been crying", "Has/been crying", "Are/crying", "Did/cry"], c: "Have/been crying" },
                { q: "The kids ___ (play) video games for hours.", o: ["have been playing", "has been playing", "are playing", "played"], c: "have been playing" },
                { q: "She ___ (not/feel) well recently.", o: ["hasn't been feeling", "haven't been feeling", "isn't feeling", "didn't feel"], c: "hasn't been feeling" },
                { q: "What ___ you ___ (do) all afternoon?", o: ["have/been doing", "has/been doing", "are/doing", "did/do"], c: "have/been doing" },
                { q: "The phone ___ (ring) for two minutes.", o: ["has been ringing", "have been ringing", "is ringing", "rang"], c: "has been ringing" },
                { q: "He ___ (study) hard for his exams.", o: ["has been studying", "have been studying", "is studying", "studied"], c: "has been studying" },
                { q: "We ___ (wait) for the bus since 2 o'clock.", o: ["have been waiting", "has been waiting", "are waiting", "waited"], c: "have been waiting" }
            ],
            "Past Simple": [
                { q: "Yesterday I ___ (go) to the park.", o: ["went", "go", "gone", "was go"], c: "went" },
                { q: "They ___ (watch) a great movie last night.", o: ["watched", "watches", "watching", "did watch"], c: "watched" },
                { q: "___ you ___ (see) Ali two days ago?", o: ["Did/see", "Do/see", "Did/saw", "Have/seen"], c: "Did/see" },
                { q: "She ___ (not/come) to the party last week.", o: ["didn't come", "doesn't come", "not came", "didn't came"], c: "didn't come" },
                { q: "We ___ (live) in Samarkand in 2020.", o: ["lived", "live", "was live", "living"], c: "lived" },
                { q: "When ___ they ___ (arrive)?", o: ["did/arrive", "do/arrive", "did/arrived", "are/arrive"], c: "did/arrive" },
                { q: "He ___ (buy) a new phone last Monday.", o: ["bought", "buyed", "buys", "buying"], c: "bought" },
                { q: "I ___ (be) very tired last night.", o: ["was", "were", "am", "been"], c: "was" },
                { q: "They ___ (be) at home yesterday.", o: ["were", "was", "are", "been"], c: "were" },
                { q: "Shakespeare ___ (write) Hamlet.", o: ["wrote", "writed", "writes", "written"], c: "wrote" },
                { q: "Did you sleep well? Yes, I ___.", o: ["did", "do", "sleped", "was"], c: "did" },
                { q: "The bus ___ (not/stop) this morning.", o: ["didn't stop", "didn't stopped", "not stopped", "doesn't stop"], c: "didn't stop" },
                { q: "I ___ (lose) my keys an hour ago.", o: ["lost", "losed", "lose", "losing"], c: "lost" },
                { q: "We ___ (meet) our teacher yesterday.", o: ["met", "meeted", "meet", "meeting"], c: "met" },
                { q: "Why ___ you ___ (leave) early yesterday?", o: ["did/leave", "did/left", "do/leave", "were/leave"], c: "did/leave" }
            ],
            "Past Continuous": [
                { q: "This time yesterday I ___ (play) tennis.", o: ["was playing", "were playing", "played", "playing"], c: "was playing" },
                { q: "What ___ you ___ (do) at 8 o'clock?", o: ["were/doing", "was/doing", "did/do", "are/doing"], c: "were/doing" },
                { q: "She ___ (cook) when the phone rang.", o: ["was cooking", "were cooking", "cooked", "is cooking"], c: "was cooking" },
                { q: "They ___ (not/study) when the lights went out.", o: ["weren't studying", "wasn't studying", "didn't study", "don't study"], c: "weren't studying" },
                { q: "I saw you in the park. You ___ (sit) on the grass.", o: ["were sitting", "was sitting", "sat", "sitting"], c: "were sitting" },
                { q: "___ it ___ (rain) when you went out?", o: ["Was/raining", "Were/raining", "Did/rain", "Is/raining"], c: "Was/raining" },
                { q: "While I ___ (work), my brother was sleeping.", o: ["was working", "were working", "worked", "am working"], c: "was working" },
                { q: "The phone rang while we ___ (have) dinner.", o: ["were having", "was having", "had", "are having"], c: "were having" },
                { q: "At midnight, the dogs outside ___ (bark).", o: ["were barking", "was barking", "barked", "are barking"], c: "were barking" },
                { q: "I ___ (not/drive) fast when the accident happened.", o: ["wasn't driving", "weren't driving", "didn't drive", "not driving"], c: "wasn't driving" },
                { q: "What ___ he ___ (wear) at the party?", o: ["was/wearing", "were/wearing", "did/wear", "is/wear"], c: "was/wearing" },
                { q: "The sun ___ (shine) when I woke up.", o: ["was shining", "were shining", "shone", "is shining"], c: "was shining" },
                { q: "We ___ (talk) about him when he walked in.", o: ["were talking", "was talking", "talked", "are talking"], c: "were talking" },
                { q: "She ___ (not/listen) to the teacher during dars.", o: ["wasn't listening", "weren't listening", "didn't listen", "not listening"], c: "wasn't listening" },
                { q: "The birds ___ (sing) beautifully all morning.", o: ["were singing", "was singing", "sang", "are singing"], c: "were singing" }
            ],
            "Past Perfect": [
                { q: "When I arrived, the train ___ (already/leave).", o: ["had already left", "has already left", "already left", "left"], c: "had already left" },
                { q: "She didn't pass the exam because she ___ (not/study).", o: ["hadn't studied", "hasn't studied", "didn't study", "not studied"], c: "hadn't studied" },
                { q: "___ you ___ (finish) cooking before guests came?", o: ["Had/finished", "Has/finished", "Did/finish", "Have/finished"], c: "Had/finished" },
                { q: "The house was dirty because we ___ (not/clean) it.", o: ["hadn't cleaned", "hasn't cleaned", "didn't clean", "haven't cleaned"], c: "hadn't cleaned" },
                { q: "He went to sleep after he ___ (watch) the news.", o: ["had watched", "has watched", "watched", "watching"], c: "had watched" },
                { q: "I didn't recognize him because he ___ (change) a lot.", o: ["had changed", "has changed", "changed", "was changed"], c: "had changed" },
                { q: "By the time we got there, the movie ___ (start).", o: ["had started", "has started", "started", "was started"], c: "had started" },
                { q: "___ she ___ (live) in China before she came here?", o: ["Had/lived", "Has/lived", "Did/live", "Was/living"], c: "Had/lived" },
                { q: "I was sure I ___ (see) that man before.", o: ["had seen", "has seen", "saw", "see"], c: "had seen" },
                { q: "We couldn't buy a ticket because we ___ (lose) money.", o: ["had lost", "has lost", "lost", "have lost"], c: "had lost" },
                { q: "The phone rang after she ___ (leave) the room.", o: ["had left", "has left", "left", "was leaving"], c: "had left" },
                { q: "He failed the test because he ___ (make) many errors.", o: ["had made", "has made", "made", "did make"], c: "had made" },
                { q: "___ they ___ (buy) a house before they married?", o: ["Had/bought", "Has/bought", "Did/buy", "Have/bought"], c: "Had/bought" },
                { q: "I thanked her for the book she ___ (lend) me.", o: ["had lent", "has lent", "lent", "lended"], c: "had lent" },
                { q: "The grass was yellow because it ___ (not/rain) all summer.", o: ["hadn't rained", "hasn't rained", "didn't rain", "not rained"], c: "hadn't rained" }
            ],
            "Past Perfect Continuous": [
                { q: "I ___ (wait) for an hour before the bus came.", o: ["had been waiting", "has been waiting", "was waiting", "waited"], c: "had been waiting" },
                { q: "She was tired because she ___ (dance) all night.", o: ["had been dancing", "has been dancing", "was dancing", "danced"], c: "had been dancing" },
                { q: "How long ___ you ___ (live) there before it closed?", o: ["had/been living", "has/been living", "were/living", "did/live"], c: "had/been living" },
                { q: "The ground was wet. It ___ (rain) for hours.", o: ["had been raining", "has been raining", "was raining", "rained"], c: "had been raining" },
                { q: "They ___ (play) football before it started snowing.", o: ["had been playing", "has been playing", "were playing", "played"], c: "had been playing" },
                { q: "He failed because he ___ (not/attend) classes.", o: ["hadn't been attending", "hasn't been attending", "wasn't attending", "didn't attend"], c: "hadn't been attending" },
                { q: "The orchestra ___ (perform) for minutes when fire started.", o: ["had been performing", "has been performing", "was performing", "performed"], c: "had been performing" },
                { q: "My eyes hurt because I ___ (read) in poor light.", o: ["had been reading", "has been reading", "was reading", "read"], c: "had been reading" },
                { q: "___ she ___ (study) long before she took the exam?", o: ["Had/been studying", "Has/been studying", "Was/studying", "Did/study"], c: "Had/been studying" },
                { q: "The kitchen was dirty. They ___ (cook) since morning.", o: ["had been cooking", "has been cooking", "were cooking", "cooked"], c: "had been cooking" },
                { q: "We ___ (drive) for hours before we found a hotel.", o: ["had been driving", "has been driving", "were driving", "drove"], c: "had been driving" },
                { q: "He was out of breath. He ___ (run) for miles.", o: ["had been running", "has been running", "was running", "ran"], c: "had been running" },
                { q: "The phone ___ (ring) for long before I answered.", o: ["had been ringing", "has been ringing", "was ringing", "rang"], c: "had been ringing" },
                { q: "They ___ (argue) for an hour when I walked in.", o: ["had been arguing", "has been arguing", "were arguing", "argued"], c: "had been arguing" },
                { q: "She ___ (not/feel) well for days before visiting doc.", o: ["hadn't been feeling", "hasn't been feeling", "wasn't feeling", "didn't feel"], c: "hadn't been feeling" }
            ],
            "Future Simple": [
                { q: "I think it ___ (rain) tomorrow.", o: ["will rain", "rains", "is raining", "rained"], c: "will rain" },
                { q: "___ you ___ (help) me with this box?", o: ["Will/help", "Do/help", "Are/help", "Shall/helping"], c: "Will/help" },
                { q: "She ___ (not/come) to school next Monday.", o: ["will not come", "doesn't come", "is not coming", "not come"], c: "will not come" },
                { q: "I promise I ___ (call) you tonight.", o: ["will call", "call", "am calling", "called"], c: "will call" },
                { q: "They ___ (arrive) at 6 o'clock tomorrow.", o: ["will arrive", "arrives", "arriving", "arrived"], c: "will arrive" },
                { q: "Where ___ you ___ (go) next summer?", o: ["will/go", "do/go", "are/going", "shall/go"], c: "will/go" },
                { q: "Wait! I ___ (carry) that bag for you.", o: ["will carry", "carry", "am carrying", "carried"], c: "will carry" },
                { q: "The exhibition ___ (close) next Sunday.", o: ["will close", "closes", "closing", "closed"], c: "will close" },
                { q: "___ she ___ (pass) the exam, what do you think?", o: ["Will/pass", "Does/pass", "Is/passing", "Will/passed"], c: "Will/pass" },
                { q: "We ___ (not/forget) your kindness.", o: ["won't forget", "don't forget", "aren't forgetting", "not forget"], c: "won't forget" },
                { q: "I ___ (be) 18 years old next year.", o: ["will be", "am", "shall being", "to be"], c: "will be" },
                { q: "The plane ___ (take off) in ten minutes.", o: ["will take off", "takes off", "taking off", "took off"], c: "will take off" },
                { q: "Do you think they ___ (win) the match?", o: ["will win", "win", "wins", "are winning"], c: "will win" },
                { q: "I ___ (not/use) this computer tomorrow.", o: ["won't use", "don't use", "am not using", "not will use"], c: "won't use" },
                { q: "Perhaps we ___ (meet) again someday.", o: ["will meet", "meet", "are meeting", "met"], c: "will meet" }
            ],
            "Future Continuous": [
                { q: "This time tomorrow I ___ (fly) to Paris.", o: ["will be flying", "will fly", "am flying", "shall flying"], c: "will be flying" },
                { q: "What ___ you ___ (do) at 10 o'clock tomorrow?", o: ["will/be doing", "will/do", "are/doing", "do/do"], c: "will/be doing" },
                { q: "She ___ (sleep) when you arrive tonight.", o: ["will be sleeping", "will sleep", "is sleeping", "sleeps"], c: "will be sleeping" },
                { q: "They ___ (not/work) during the weekend.", o: ["won't be working", "won't work", "aren't working", "don't work"], c: "won't be working" },
                { q: "Good luck! We ___ (think) of you tomorrow.", o: ["will be thinking", "will think", "are thinking", "shall think"], c: "will be thinking" },
                { q: "___ it ___ (rain) when we leave the building?", o: ["Will/be raining", "Will/rain", "Is/raining", "Does/rain"], c: "Will/be raining" },
                { q: "Don't phone me between 2 and 3. We ___ (have) a meeting.", o: ["will be having", "will have", "are having", "have"], c: "will be having" },
                { q: "At noon tomorrow, he ___ (drive) across the desert.", o: ["will be driving", "will drive", "is driving", "drives"], c: "will be driving" },
                { q: "They ___ (sit) in the classroom at this time next week.", o: ["will be sitting", "will sit", "are sitting", "sit"], c: "will be sitting" },
                { q: "I ___ (not/use) my car tomorrow, you can take it.", o: ["won't be using", "won't use", "am not using", "don't use"], c: "won't be using" },
                { q: "___ she ___ (watch) TV when we get home?", o: ["Will/be watching", "Will/watch", "Is/watching", "Does/watch"], c: "Will/be watching" },
                { q: "The kids ___ (play) in the garden all afternoon.", o: ["will be playing", "will play", "are playing", "play"], c: "will be playing" },
                { q: "We ___ (celebrate) our victory this time tomorrow.", o: ["will be celebrating", "will celebrate", "are celebrating", "celebrate"], c: "will be celebrating" },
                { q: "He ___ (not/study) tonight, he is going to cinema.", o: ["won't be studying", "won't study", "isn't studying", "doesn't study"], c: "won't be studying" },
                { q: "This time next month, you ___ (enjoy) holidays.", o: ["will be enjoying", "will enjoy", "are enjoying", "enjoy"], c: "will be enjoying" }
            ],
            "Future Perfect": [
                { q: "By next year, I ___ (finish) university.", o: ["will have finished", "will finish", "have finished", "will be finishing"], c: "will have finished" },
                { q: "She ___ (complete) the project by tomorrow noon.", o: ["will have completed", "will complete", "has completed", "will be completing"], c: "will have completed" },
                { q: "___ you ___ (do) all work by 6 o'clock?", o: ["Will/have done", "Will/do", "Have/done", "Will/be doing"], c: "Will/have done" },
                { q: "They ___ (not/arrive) by dinner time, they are late.", o: ["won't have arrived", "won't arrive", "haven't arrived", "won't be arriving"], c: "won't have arrived" },
                { q: "By 2030, scientists ___ (find) a cure for this virus.", o: ["will have found", "will find", "have found", "will be finding"], c: "will have found" },
                { q: "In two years' time, we ___ (build) our new house.", o: ["will have built", "will build", "have built", "will be building"], c: "will have built" },
                { q: "___ he ___ (write) the book before the deadline?", o: ["Will/have written", "Will/write", "Has/written", "Will/be writing"], c: "Will/have written" },
                { q: "I ___ (not/save) enough money by this winter.", o: ["won't have saved", "won't save", "haven't saved", "won't be saving"], c: "won't have saved" },
                { q: "By tomorrow morning, the snow ___ (melt).", o: ["will have melted", "will melt", "has melted", "will be melting"], c: "will have melted" },
                { q: "They ___ (leave) England by next week.", o: ["will have left", "will leave", "have left", "will be leaving"], c: "will have left" },
                { q: "___ you ___ (read) the whole novel by tomorrow?", o: ["Will/have read", "Will/read", "Have/read", "Will/be reading"], c: "Will/have read" },
                { q: "By the end of this month, I ___ (live) here for a year.", o: ["will have lived", "will live", "have lived", "will be living"], c: "will have lived" },
                { q: "The meeting ___ (end) by the time you get here.", o: ["will have ended", "will end", "ends", "will be ending"], c: "will have ended" },
                { q: "She ___ (not/marry) him by next summer.", o: ["won't have married", "won't marry", "hasn't married", "won't be marrying"], c: "won't have married" },
                { q: "By midnight, they ___ (solve) the puzzle.", o: ["will have solved", "will solve", "have solved", "will be solving"], c: "will have solved" }
            ],
            "Future Perfect Continuous": [
                { q: "By 5 o'clock, I ___ (wait) for three hours.", o: ["will have been waiting", "will be waiting", "have been waiting", "will wait"], c: "will have been waiting" },
                { q: "She ___ (work) here for ten years by next month.", o: ["will have been working", "will be working", "has been working", "will work"], c: "will have been working" },
                { q: "How long ___ you ___ (study) when you graduate?", o: ["will/have been studying", "will/be studying", "have/been studying", "will/study"], c: "will/have been studying" },
                { q: "They ___ (travel) for 24 hours by tomorrow morning.", o: ["will have been traveling", "will be traveling", "have been traveling", "will travel"], c: "will have been traveling" },
                { q: "By next Sunday, it ___ (rain) for a whole week.", o: ["will have been raining", "will be raining", "has been raining", "will rain"], c: "will have been raining" },
                { q: "He ___ (not/live) here long enough to know people.", o: ["won't have been living", "won't be living", "haven't been living", "won't live"], c: "won't have been living" },
                { q: "By dinner time, she ___ (cook) for four hours.", o: ["will have been cooking", "will be cooking", "has been cooking", "will cook"], c: "will have been cooking" },
                { q: "The engine ___ (run) for hours by the time we arrive.", o: ["will have been running", "will be running", "has been running", "will run"], c: "will have been running" },
                { q: "___ you ___ (drive) long before you take a break?", o: ["Will/have been driving", "Will/be driving", "Have/been driving", "Will/drive"], c: "Will/have been driving" },
                { q: "By next month, they ___ (learn) English for two years.", o: ["will have been learning", "will be learning", "have been learning", "will learn"], c: "will have been learning" },
                { q: "I ___ (play) guitar for an hour by 9 PM.", o: ["will have been playing", "will be playing", "have been playing", "will play"], c: "will have been playing" },
                { q: "She ___ (not/sleep) enough if she continues working.", o: ["won't have been sleeping", "won't be sleeping", "hasn't been sleeping", "won't sleep"], c: "won't have been sleeping" },
                { q: "By midnight, we ___ (dance) for five hours.", o: ["will have been dancing", "will be dancing", "have been dancing", "will dance"], c: "will have been dancing" },
                { q: "How long ___ he ___ (teach) by the end of this term?", o: ["will/have been teaching", "will/be teaching", "has/been teaching", "will/teach"], c: "will/have been teaching" },
                { q: "They ___ (talk) on phone for an hour by 10 o'clock.", o: ["will have been talking", "will be talking", "have been talking", "will talk"], c: "will have been talking" }
            ]
        };

        // Mavzular selektini to'ldirish
        const topicSelect = document.getElementById('main-topic');
        Object.keys(autoTestDatabase).forEach(tense => {
            let opt = document.createElement('option');
            opt.value = tense;
            opt.innerText = tense + " darsi";
            topicSelect.appendChild(opt);
        });

        // Bugungi sanani avtomat joylash
        document.getElementById('main-date').value = new Date().toISOString().split('T')[0];

        let database = JSON.parse(localStorage.getItem('skillcard_v6_db')) || {};

        const mainDateInput = document.getElementById('main-date');
        const timeline = document.getElementById('timeline');
        const fAll = document.getElementById('f-all');
        const fToday = document.getElementById('f-today');
        let currentFilter = 'all';

        // Massivni aralashtirish (Fisher-Yates)
        function shuffleArray(array) {
            let shuffled = [...array];
            for (let i = shuffled.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];
            }
            return shuffled;
        }

        // Dars yaratish va 15 ta testni generatsiya qilish
        document.getElementById('generate-day-btn').addEventListener('click', () => {
            const date = mainDateInput.value;
            const topic = topicSelect.value;
            const cardQ = document.getElementById('card-q').value.trim();
            const cardA = document.getElementById('card-a').value.trim();

            if (!date) { alert("Iltimos, sanani tanlang!"); return; }

            if (!database[date]) {
                const presetTests = autoTestDatabase[topic] || [];
                
                // IDX barcha elementlarga beriladi, aralashganda ham chalkashmaslik kafolati!
                const configuredTests = presetTests.map((t, index) => {
                    // Variantlarni obyekt qilib chiqamiz, shunda matn o'zgarsa ham ID orqali tekshiriladi
                    const mappedOptions = t.o.map((o, oIdx) => ({ id: oIdx, text: o, isCorrect: o === t.c }));
                    return {
                        id: index,
                        q: t.q,
                        options: mappedOptions,
                        shuffledOptions: shuffleArray(mappedOptions) // Vizual tasodifiy tartib
                    };
                });

                database[date] = {
                    date: date,
                    topic: topic,
                    cards: [],
                    tests: configuredTests,
                    userAnswers: {} // Kalit: Savol_ID, Qiymat: Tanlangan_Variant_ID
                };
            } else {
                database[date].topic = topic;
            }

            if (cardQ && cardA) {
                database[date].cards.push({ q: cardQ, a: cardA });
            }

            save();
            render();

            document.getElementById('card-q').value = '';
            document.getElementById('card-a').value = '';
        });

        function deleteDayBlock(dateStr) {
            delete database[dateStr];
            save();
            render();
        }

        // Test Bosilganda ishlaydigan 100% ishonchli funksiya
        function checkTestAnswer(dateStr, testId, optionId, btn) {
            const day = database[dateStr];
            if (!day || day.userAnswers[testId] !== undefined) return; // Allaqachon bosilgan bo'lsa qayta ishlamaydi

            day.userAnswers[testId] = optionId;
            save();

            const parent = btn.parentElement;
            const buttons = parent.querySelectorAll('.opt-btn');

            // Tugmalarni ranglash logicasi
            buttons.forEach(b => {
                const bOptId = parseInt(b.getAttribute('data-opt-id'));
                const isCorrect = b.getAttribute('data-is-correct') === 'true';
                
                if (isCorrect) {
                    b.classList.add('correct'); // To'g'ri javob doim yashil bo'ladi
                }
                if (bOptId === optionId && !isCorrect) {
                    b.classList.add('wrong'); // Agar foydalanuvchi noto'g'risini bossa qizil bo'ladi
                }
            });
        }

        function save() {
            localStorage.setItem('skillcard_v6_db', JSON.stringify(database));
        }

        function render() {
            timeline.innerHTML = '';
            const todayStr = new Date().toISOString().split('T')[0];

            let keys = Object.keys(database);
            if (currentFilter === 'today') {
                keys = keys.filter(k => k === todayStr);
            }

            if (keys.length === 0) {
                timeline.innerHTML = '<div class="empty-state">Hozircha hech qaysi kunga dars generatsiya qilinmagan. Yuqoridan dars yaratib ko\'ring!</div>';
                return;
            }

            keys.sort((a, b) => new Date(b) - new Date(a));

            keys.forEach(dateKey => {
                const dayData = database[dateKey];
                const dayBox = document.createElement('div');
                dayBox.classList.add('day-box');

                const d = new Date(dateKey);
                const formattedDate = d.toLocaleDateString('uz-UZ', { day: 'numeric', month: 'long', year: 'numeric' });

                let html = `
                    <div class="day-header">
                        <div class="day-date">📅 ${formattedDate}</div>
                        <div style="display:flex; gap:1rem; align-items:center;">
                            <span class="day-topic">${dayData.topic}</span>
                            <button onclick="deleteDayBlock('${dateKey}')" style="background:none; border:1px solid #ef4444; color:#ef4444; padding:0.3rem 0.6rem; border-radius:8px; font-size:0.85rem;">O'chirish</button>
                        </div>
                    </div>
                `;

                // Flashcards
                if (dayData.cards.length > 0) {
                    html += `<div class="cards-grid">`;
                    dayData.cards.forEach(card => {
                        html += `
                            <div class="flashcard" onclick="this.classList.toggle('flipped')">
                                <div class="card-inner">
                                    <div class="card-front"><p>${card.q}</p></div>
                                    <div class="card-back"><p>${card.a}</p></div>
                                </div>
                            </div>
                        `;
                    });
                    html += `</div>`;
                }

                // 15 interaktiv testlar bloki
                if (dayData.tests.length > 0) {
                    html += `
                        <div class="test-section">
                            <h4 style="color:#c084fc; margin-bottom:1rem;">📝 ${dayData.topic} bo'yicha 15 talik imtihon</h4>
                    `;

                    dayData.tests.forEach((test) => {
                        const savedAnsOptId = dayData.userAnswers[test.id];

                        html += `
                            <div class="test-card">
                                <div><strong>${test.id + 1}.</strong> ${test.q}</div>
                                <div class="options-layout">
                        `;

                        test.shuffledOptions.forEach(opt => {
                            let cls = '';
                            if (savedAnsOptId !== undefined) {
                                if (opt.isCorrect) cls = 'correct';
                                else if (opt.id === savedAnsOptId) cls = 'wrong';
                            }
                            
                            html += `
                                <button class="opt-btn ${cls}" 
                                    data-opt-id="${opt.id}" 
                                    data-is-correct="${opt.isCorrect}"
                                    onclick="checkTestAnswer('${dateKey}', ${test.id}, ${opt.id}, this)">
                                    ${opt.text}
                                </button>
                            `;
                        });

                        html += `
                                </div>
                            </div>
                        `;
                    });

                    html += `</div>`;
                }

                dayBox.innerHTML = html;
                timeline.appendChild(dayBox);
            });
        }

        fAll.addEventListener('click', () => {
            fAll.classList.add('active'); fToday.classList.remove('active');
            currentFilter = 'all'; render();
        });
        fToday.addEventListener('click', () => {
            fToday.classList.add('active'); fAll.classList.remove('active');
            currentFilter = 'today'; render();
        });

        render();
    </script>
</body>
</html>
